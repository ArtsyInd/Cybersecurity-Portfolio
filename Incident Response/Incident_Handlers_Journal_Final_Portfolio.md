# Incident Handler's Journal
## Google Cybersecurity Certificate — Detection and Response

**Portfolio purpose:** This journal records incident investigations, cybersecurity tool use, and reflections from the course. It is written from the perspective of a developing cybersecurity professional.

---

## Journal Entry 1 — Ransomware Incident at a Primary-Care Clinic

**Date:** October 10, 2026  
**Entry:** 1  
**Description (50–80 words):**

I reviewed a ransomware incident affecting a small primary-care clinic in the United States. A staff member opened a phishing attachment, after which ransomware encrypted critical files, including patient data, and displayed a ransom note. This entry documents the incident using the 5 Ws and considers the Detection and Analysis and Containment, Eradication, and Recovery phases of the NIST Incident Response Lifecycle.

### The 5 Ws

- **Who caused the incident?** The scenario attributes the incident to an organized group known for targeting healthcare and transportation organizations. The identity of individual operators was not provided.
- **What happened?** A targeted phishing email delivered an attachment that led to ransomware being installed. Critical files and patient data were encrypted, and a ransom note demanded payment.
- **When did it happen?** The incident began on a Tuesday at approximately 9:00 a.m. The calendar date was not specified.
- **Where did it happen?** At a small primary-care clinic in the United States.
- **Why did it happen?** The initial access vector was a phishing attachment. The scenario indicates that the attackers targeted the clinic, but it does not establish their full motive beyond the ransom demand.

### Response considerations

The clinic shut down its systems. This is a containment-related action intended to limit further impact. The scenario did not provide details about eradication, restoration, backup recovery, or whether the ransom was paid, so I would not record those actions as completed.

### Key learning

This incident reinforced the importance of employee awareness, email security, endpoint protection, reliable backups, and a rehearsed ransomware response plan. Healthcare organizations must also consider patient-care continuity when responding to an incident.

---

## Journal Entry 2 — Phishing Incident Involving a Malicious Attachment

**Date:** October 28, 2026  
**Entry:** 2  
**Description (50–80 words):**

I investigated a phishing alert at a financial services company after an employee downloaded and opened an email attachment that had already been verified as malicious by its SHA-256 hash. Unauthorized executable files appeared shortly afterward, and the intrusion detection system (IDS) generated an alert. This investigation covered Detection and Analysis and led to an escalation decision.

### The 5 Ws

- **Who caused the incident?** The email sender initiated the attack, but the sender's identity and the individual threat actor were not established in the available ticket details.
- **What happened?** An employee received a phishing email, downloaded and opened its malicious attachment, and multiple unauthorized executable files were created on the computer.
- **When did it happen?** The email arrived at 1:11 p.m.; the attachment was downloaded and opened at 1:13 p.m.; unauthorized executable files were created at 1:15 p.m.; and the IDS alert reached the SOC at 1:20 p.m. The calendar date was not supplied.
- **Where did it happen?** On the recipient employee's computer at a financial services company. The hostname and exact network location were not provided.
- **Why did it happen?** The attacker used a phishing email to deliver a malicious attachment. Opening the attachment was followed by unauthorized executable-file creation, indicating possible endpoint compromise.

### Indicators and evidence

- **SHA-256:** `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`
- **Observed behavior:** Multiple unauthorized executable files were created after the attachment was opened.
- **Detection source:** The IDS detected the files and sent an alert to the SOC.

### Assessment and disposition

**Decision: Escalate.** The attachment was verified as malicious, the employee opened it, and suspicious executable files were created shortly afterward. These facts support escalation to the incident response team for endpoint investigation, containment, and remediation. The available information does not establish whether data was accessed or exfiltrated.

---

## Journal Entry 3 — Using VirusTotal to Investigate a Suspicious File Hash

**Date:** October 28, 2026  
**Entry:** 3  
**Description (50–80 words):**

I used VirusTotal as a threat-intelligence resource to investigate the SHA-256 hash associated with a suspicious email attachment. The purpose was to review security-vendor detections and available file intelligence before making an assessment. The hash was verified as malicious in the course activity, supporting the decision to treat the phishing alert as a genuine security concern and escalate it.

### Tool(s) used

**VirusTotal**

- Searched for the SHA-256 file hash: `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`.
- Reviewed the file's detection information and available report details to assess whether security vendors identified it as malicious.
- Used the hash as a file indicator to connect the threat-intelligence finding with the phishing alert.
- Treated the result as one source of evidence rather than relying on a single vendor verdict.

### Findings and considerations

The course activity states that the file hash had been verified as malicious. This finding supported escalation of the alert. A hash can help identify a known file, but it may change if the file is modified. In a live investigation, I would also preserve the original sample safely, review file metadata and behavior where authorized, and correlate findings with endpoint and network telemetry.

**Handling note:** VirusTotal submissions may be shared with the service's security community. Sensitive, confidential, or personal files should not be uploaded unless the organization's policy explicitly permits it.

---

## Journal Entry 4 — Reviewing an IDS Alert and Correlating Endpoint Activity

**Date:** October 28, 2026  
**Entry:** 4  
**Description (50–80 words):**

I reviewed the IDS alert generated during the financial-services phishing scenario and correlated its timestamp with the employee's activity. The alert was received five minutes after the malicious attachment was opened and unauthorized executable files were created. This exercise helped me understand how detection tools and event timelines support triage, prioritization, and escalation during the Detection and Analysis phase.

### Tool(s) used

**Intrusion Detection System (IDS) alert and event timeline**

- Reviewed the alert indicating that unauthorized executable files had been detected.
- Compared the alert time (1:20 p.m.) with the reported email and endpoint events.
- Established the sequence: email received at 1:11 p.m.; attachment opened at 1:13 p.m.; unauthorized executable files created at 1:15 p.m.; IDS alert at 1:20 p.m.
- Used the sequence of events to support escalation rather than treating the alert as an isolated or unexplained detection.

### Findings and considerations

The close timing between opening the attachment and the creation of unauthorized executables made the activity suspicious. The IDS alert provided a detection point for the SOC, while the endpoint timeline supplied context for triage. The exact IDS product, signature name, executable filenames, and endpoint hostname were not provided, so they are not recorded here.

**Analyst takeaway:** An alert should be investigated in context. Correlating multiple events in a timeline can help distinguish routine activity from a likely incident and provide a clear rationale for escalation.

---

# Reflections / Notes

### 1. Were there any specific activities that were challenging for you? Why or why not?

The most challenging activities were correlating incident evidence and deciding what justified escalation. It was not enough to identify a suspicious email or file; I had to connect timestamps, endpoint behavior, and detection alerts to understand the sequence of events. This helped me become more careful about separating confirmed evidence from assumptions.

### 2. Has your understanding of incident detection and response changed since taking this course?

Yes. I now understand incident response as a structured process rather than simply reacting to an alert. The NIST Incident Response Lifecycle helped me see how preparation, detection and analysis, containment, eradication and recovery, and post-incident activity fit together. I also recognize the importance of accurate documentation and communication throughout an investigation.

### 3. Was there a specific tool or concept that you enjoyed the most? Why?

I particularly enjoyed using VirusTotal to investigate a suspicious file hash because it showed how threat intelligence can support an analyst's initial assessment. I also found event timelines useful: correlating an employee's actions with IDS detections made the incident easier to understand and demonstrated why context matters during alert triage.

---

# Final Journal Review — Self-Assessment

| # | Self-assessment statement | Result |
|---|---|---|
| 1 | The journal contains at least four numbered entries with dates and descriptions. | **Yes** |
| 2 | At least two entries document incident investigations using the 5 Ws. | **Yes** |
| 3 | At least two entries describe the use of cybersecurity tools. | **Yes** |
| 4 | The Reflections / Notes section addresses all three reflection questions. | **Yes** |
| 5 | The journal has been reviewed for clarity, grammar, punctuation, and unsupported claims. | **Yes** |

## Closing Reflection

Maintaining an incident handler's journal has shown me that documentation is part of the investigation itself, not an administrative task to complete afterward. A clear record of what happened, when it happened, what evidence was reviewed, and why a decision was made helps other analysts continue the investigation. As I develop my cybersecurity skills, I want to build the habit of recording evidence carefully, communicating findings clearly, and never presenting assumptions as confirmed facts.

---

## Portfolio note

This journal is a coursework-based record. Scenario details are distinguished from confirmed findings, and unavailable information—such as exact endpoint identifiers, sender addresses, packet contents, and specific IDS product names—has not been fabricated. Before publishing, remove or redact any real organizational, personal, or confidential information if you add further evidence.
