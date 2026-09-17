# Access Control Investigation: Unauthorized Payroll Transaction

## Project Overview

This activity demonstrates how access-control analysis can be used to investigate a suspicious financial transaction and identify weaknesses in user account management and authorization.

The investigation compares information from an **Event Log** with an **Employee Directory** to identify potentially unauthorized access and recommend security controls.

---

## Scenario

I am the first cybersecurity professional at a growing business. A suspicious deposit/payment was made from the business to an unknown bank account. The finance manager confirmed that they did not make the transaction, and the payment was stopped.

My task was to review the available event and employee information, identify access-control issues, and recommend mitigations that could prevent similar incidents.

---

## 1. Notes About the User

Based on the event log, the following observations were identified:

- The suspicious event occurred on **10/03/2023**.
- The user associated with the event had the role **Legal / Administrator**.
- The event log also recorded the **IP address of the computer used to log in**.

These details are useful for correlating the suspicious activity with employee records, authentication logs, and other security telemetry.

---

## 2. Access-Control Issues Identified

After comparing the event information with the employee directory, the following issues were identified.

### Issue 1: Former Contractor Account Remained Active

**Robert Taylor, Jr.** was identified as a contractor whose contract ended in **2019**. However, the account associated with this user was still able to access payroll-related systems in **2023**.

This indicates a weakness in the organization's **user account lifecycle management**. Accounts belonging to former employees or contractors should be disabled or removed when their relationship with the organization ends.

### Issue 2: Excessive Administrative Privileges

The user account had **administrator-level access**. Administrative privileges provide access to sensitive systems and should only be granted when required for a person's job responsibilities.

Retaining administrator privileges for a former contractor creates unnecessary risk because a compromised or improperly maintained account could be used to access sensitive business resources.

---

## 3. Recommended Mitigations

### 1. Implement Automatic Account Expiration

User accounts, particularly contractor accounts, should have an expiration date.

For example:

- Contractor accounts can automatically expire after a defined period such as 30 days unless renewed.
- Accounts should be reviewed whenever an employee or contractor leaves the organization.
- Departing users should have their accounts disabled immediately.

This reduces the likelihood of dormant accounts being used to access company systems.

### 2. Apply the Principle of Least Privilege

Employees and contractors should receive only the permissions required to perform their assigned responsibilities.

For contractors specifically:

- Limit access to only necessary systems and files.
- Avoid assigning administrator privileges unless there is a documented business requirement.
- Periodically review privileged accounts.
- Remove unnecessary permissions when responsibilities change.

### 3. Enable Multi-Factor Authentication (MFA)

MFA should be enabled for payroll, financial, administrative, and other sensitive systems.

Even if an attacker obtains a user's password, MFA provides an additional authentication factor that can help prevent unauthorized access.

### 4. Perform Regular Access Reviews

The organization should periodically review:

- Active employee and contractor accounts
- Privileged accounts
- Payroll access
- Dormant accounts
- Accounts belonging to former employees or contractors

Access should be removed whenever it is no longer required.

---

## 4. Potential Threat-Actor Assessment

The former contractor account is an important lead because it remained active after the contract ended and was associated with access to payroll systems years later.

However, the available information does **not** prove that Robert Taylor, Jr. personally performed the suspicious transaction. The account could have been compromised and used by another person.

Additional investigation should therefore focus on:

- Authentication and login records
- Source IP addresses
- Device information
- VPN logs
- MFA activity
- Payroll system audit logs
- Password-reset history
- Endpoint security telemetry
- Other activity performed by the account

This distinction is important in cybersecurity investigations because an account being associated with an event does not necessarily establish who was physically responsible for the activity.

---

## 5. Security Concepts Demonstrated

### Authentication

Authentication verifies **who a user is**.

Examples include:

- Passwords
- MFA
- Security keys
- Biometric authentication

### Authorization

Authorization determines **what an authenticated user is allowed to access or perform**.

For example, a payroll administrator may have permission to process payroll, while a contractor may only need access to a limited set of resources.

### Accounting

Accounting, or auditing, records **what actions a user performed**.

Examples include:

- Login timestamps
- IP addresses
- Files accessed
- Payroll transactions
- Administrative changes

Effective security requires all three areas to work together.

---

## 6. User Lifecycle Management

A secure user lifecycle should include controls throughout the user's relationship with the organization:

**Join → Access Granted → Access Reviewed → Role Changed → Contract/Employment Ends → Access Revoked**

For contractors and employees leaving the organization, accounts should be disabled promptly and associated privileges should be removed.

Regular access reviews can also identify dormant accounts and excessive permissions before they are abused.

---

## 7. Risk Reduction

| Security weakness | Recommended control | Risk reduced |
|---|---|---|
| Former contractor account remains active | Automatic account expiration and offboarding | Unauthorized account use |
| Excessive administrative privileges | Least privilege | Unauthorized system changes |
| Stolen passwords | MFA | Account takeover |
| Unreviewed access | Periodic access reviews | Excessive or outdated permissions |
| Limited visibility into activity | Audit logging | Difficult incident investigation |

---

## Conclusion

This investigation demonstrates how access-control weaknesses can contribute to security incidents involving sensitive financial systems.

The key issues identified were the continued access of a former contractor account and the presence of excessive administrative privileges. Implementing **automatic account expiration, least privilege, MFA, and regular access reviews** would strengthen the organization's access-control posture and reduce the risk of unauthorized activity.

The investigation also highlights the importance of distinguishing between an account being associated with suspicious activity and proving who actually performed the activity. Strong authentication, authorization, and audit logging provide the evidence needed to investigate such incidents accurately.
