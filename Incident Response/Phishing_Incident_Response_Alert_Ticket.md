# Phishing Incident Response: Alert Ticket

## Activity Overview

**Role:** Level 1 Security Operations Center (SOC) Analyst  
**Incident type:** Phishing email with a malicious attachment  
**Ticket status:** **Escalated**  
**Disposition:** Escalate for further incident response

> **Scope note:** This coursework scenario confirms that the email attachment was verified as malicious using its SHA-256 hash. The exact sender address, subject line, employee name, endpoint identifier, and severity shown in the original alert-ticket template were not included in the activity text provided here. They are not invented in this write-up.

## 1. Alert Evaluation

The alert concerns a suspicious email attachment that an employee downloaded and opened. The attachment's SHA-256 hash was investigated in the preceding activity and verified as malicious. Because the file was opened and malicious activity was subsequently observed, this should be treated as a credible security incident rather than a false positive.

### Relevant timeline

| Time | Event |
|---|---|
| 1:11 p.m. | Email with the attachment was received. |
| 1:13 p.m. | The attachment was downloaded and opened. |
| 1:15 p.m. | Multiple unauthorized executable files were created. |
| 1:20 p.m. | The intrusion detection system (IDS) detected the files and sent an alert to the SOC. |

### Evidence to review in the original alert ticket

- **Severity:** Review the severity recorded in the ticket. The playbook indicates that Medium or High severity is a reason to consider escalation.
- **Sender and message:** Compare the sender's display name and email address, and inspect the subject and message body for impersonation, unusual requests, or other phishing indicators. The exact sender and message content are not included in the supplied activity description.
- **Attachment:** The email contained an attachment, and its hash has already been verified as malicious.
- **Endpoint activity:** Multiple unauthorized executable files were created shortly after the attachment was opened.

## 2. The Five Ws

**Who caused the incident?**  
The specific threat actor has not been identified from the supplied details. The incident began with a phishing email sent to an employee; the sender's identity should be verified using the original alert and email headers.

**What happened?**  
An employee downloaded and opened a malicious email attachment. Multiple unauthorized executable files were then created on the employee's computer, triggering an IDS alert to the SOC.

**When did it happen?**  
The email arrived at 1:11 p.m., the attachment was downloaded and opened at 1:13 p.m., unauthorized executables were created at 1:15 p.m., and the IDS alert was generated at 1:20 p.m. The calendar date was not included in the provided scenario text.

**Where did it happen?**  
The incident occurred on the recipient employee's computer at the financial services company. The exact hostname, device identifier, and network location should be taken from the original alert ticket.

**Why did it happen?**  
The initial access appears to have occurred through a phishing email and its malicious attachment. Opening the attachment allowed malicious activity to occur on the endpoint. The precise delivery method and the attacker's objective require further investigation.

## 3. Indicators and Assessment

- **SHA-256 file hash:** `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`
- **Observed behavior:** Multiple unauthorized executable files were created after the attachment was opened.
- **Detection:** The IDS detected the files and generated an alert for the SOC.

The hash is the principal file indicator supplied for this activity. The endpoint behavior and IDS alert provide additional evidence that the event requires investigation. No unverified sender address, IP address, or domain is asserted here.

## 4. Escalation Decision

**Decision: Escalate the alert.**

Reasons:

1. **The attachment has been verified as malicious.** This supports treating the alert as a genuine security concern rather than closing it as a false positive.
2. **The employee opened the attachment.** The file was not merely received; it was downloaded and opened, creating a credible possibility of endpoint compromise.
3. **Suspicious endpoint activity followed.** Multiple unauthorized executable files were created two minutes after the attachment was opened, and the IDS raised an alert five minutes after that. This sequence warrants further investigation and containment by the appropriate incident response team.

## 5. Ticket Comments

> **Recommended ticket status: Escalated**
>
> Investigated a phishing alert involving an email attachment whose SHA-256 hash was verified as malicious in the preceding analysis. The employee received the email at 1:11 p.m. and downloaded and opened the attachment at 1:13 p.m.; multiple unauthorized executable files were created at 1:15 p.m., and the IDS alerted the SOC at 1:20 p.m. The alert is being escalated because the attachment is confirmed malicious, it was opened by the recipient, and suspicious executable-file creation occurred shortly afterward. Further incident response is required to investigate the affected endpoint, determine the extent of any compromise, and contain and remediate the threat.

## 6. Recommended Next Actions

These are recommended follow-up actions for the incident response team, not actions confirmed as completed during this coursework exercise:

1. Follow the organization's containment procedure for the affected endpoint.
2. Preserve the email, attachment metadata, endpoint logs, IDS alert, and relevant timestamps for investigation.
3. Search for the same file hash and related activity across other endpoints and email records.
4. Investigate the newly created executables and any subsequent process, persistence, network, or credential-related activity.
5. Remove the malicious email from other mailboxes where applicable, block confirmed indicators using approved controls, and remediate the affected endpoint according to organizational policy.
6. Document the investigation, containment, recovery, and lessons learned in the incident ticket and incident handler's journal.

## 7. Incident Handler's Journal Entry

**Summary:** A phishing email delivered an attachment that was subsequently verified as malicious. The recipient opened it, unauthorized executable files appeared, and the IDS generated an alert.

**Key evidence:** SHA-256 `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`; event sequence from 1:11 p.m. to 1:20 p.m.; IDS detection of unauthorized executable files.

**Assessment:** The alert is credible and should be escalated. The available information does not establish the attacker's identity, the full scope of compromise, or whether data was accessed or exfiltrated.

**Next steps:** Escalate according to the phishing playbook, preserve evidence, investigate the endpoint and related indicators, and record the incident response team's findings.

## Conclusion

I would escalate this alert rather than close it. The confirmed malicious attachment, the employee opening the file, and the subsequent creation of unauthorized executable files provide three clear reasons for further incident response. The ticket should remain factual: the activity described above is supported by the scenario, while containment and remediation are recommended next steps and should not be marked complete until verified.
