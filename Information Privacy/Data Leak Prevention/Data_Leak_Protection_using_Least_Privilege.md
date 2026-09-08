# Data Leak Worksheet — Least Privilege and Information Privacy

> **Cybersecurity Portfolio Project**  
> **Framework:** NIST Cybersecurity Framework (CSF) / NIST SP 800-53  
> **Control:** AC-6 — Least Privilege  
> **Category:** Information Privacy | Access Control | Data Protection

---

## Activity Overview

This assessment examines a data leak at an educational technology company and evaluates whether the company's access controls support information privacy. The investigation focuses on the **principle of least privilege**, which requires users to receive only the access necessary to perform their assigned tasks.

---

# Incident Scenario

An educational technology company developed an application that automatically grades assignments and handles data from academic institutions, instructors, parents, and students.

A data leak occurred when an employee accidentally shared confidential internal business plans with an external business partner during a sales call. The shared folder contained information associated with a new product offering, including customer analytics and marketing materials.

The incident occurred because:

1. A manager gave a customer success representative access to an internal folder.
2. The folder contained more information than the representative needed.
3. The manager forgot to remove or unshare the folder.
4. The representative intended to share only marketing materials.
5. The representative accidentally shared a link to the entire folder.
6. The business partner subsequently posted the link on social media.

---

# 1. Issues

The data leak resulted from excessive access to an internal folder and a failure to remove access when it was no longer needed. The employee also unintentionally shared the entire folder instead of the intended marketing materials, allowing confidential business information to reach an external partner and ultimately social media.

---

# 2. Review — NIST SP 800-53 AC-6

NIST SP 800-53 AC-6 addresses **least privilege**, requiring organizations to limit users' access to only the information and resources necessary for their assigned tasks. The control supports stronger access management by defining appropriate privileges, limiting unnecessary access, and using control enhancements to strengthen authorization practices.

NIST defines least privilege as restricting users or processes to the minimum system authorizations and resources needed to perform assigned tasks.

---

# 3. Recommendations

Based on the AC-6 guidance provided for this activity, I recommend the following two improvements.

## Recommendation 1 — Restrict Access to Sensitive Resources Based on User Role

Access to sensitive internal resources should be assigned according to the employee's role and business need. A customer success representative who only needs marketing materials should not automatically receive access to a folder containing confidential product plans and customer analytics.

**Implementation approach:**

- Define access roles for sensitive information.
- Grant access only to users who require it for their job responsibilities.
- Separate confidential business documents from materials intended for external sharing.
- Use role-based access controls where appropriate.
- Review access when an employee's responsibilities change.

This directly supports the principle of least privilege by reducing unnecessary access to sensitive information.

---

## Recommendation 2 — Automatically Revoke Access to Information After a Defined Period

Temporary access to sensitive folders should expire automatically after a defined period instead of relying entirely on employees or managers to remember to remove access.

**Implementation approach:**

- Set expiration dates for temporary access.
- Use time-limited sharing links where supported.
- Require reauthorization when temporary access expires.
- Remove access automatically when the approved period ends.
- Apply shorter expiration periods to highly sensitive information.

This would have reduced the risk created when the manager forgot to unshare the folder.

---

# 4. Justification

Role-based access would have limited the representative's access to only the information required for the sales activity, reducing exposure to confidential documents. Automatically expiring temporary access would also reduce dependence on human memory and prevent outdated permissions from remaining active, directly addressing the manager's failure to unshare the folder.

---

# Control-to-Incident Mapping

| Incident Problem | Recommended Control | Security Benefit |
|---|---|---|
| Representative received access to unnecessary internal documents | Restrict access based on user role | Reduces excessive permissions |
| Manager forgot to unshare the folder | Automatic access expiration | Removes temporary access without relying on memory |
| Entire folder was shared instead of specific materials | Separate sensitive resources from externally shareable content | Reduces accidental disclosure |
| External partner received access to internal information | Least-privilege access model | Limits who can access sensitive resources |
| Access remained available after the original need | Time-limited access | Reduces persistent or stale permissions |

---

# Applying the Principle of Least Privilege

A safer access model would be:

```text
Employee Role
     |
     v
Business Need
     |
     v
Required Information
     |
     v
Minimum Necessary Access
     |
     v
Time-Limited Authorization
     |
     v
Automatic Revocation
```

Instead of giving the representative access to the entire internal folder, the organization should provide access only to the specific marketing resources required for the sales activity.

---

# Preventive Data Handling Process

### 1. Classify the Information

Identify whether a document contains public, internal, confidential, or restricted information.

### 2. Assign Access Based on Role

Determine which employees require access based on their responsibilities.

### 3. Limit the Scope of Access

Provide access to the smallest appropriate folder, document, or resource rather than a broader collection of information.

### 4. Set an Expiration

Temporary access should automatically expire when the business need ends.

### 5. Review Permissions

Regularly audit access permissions to identify excessive or outdated access.

### 6. Monitor External Sharing

Monitor and, where possible, restrict sharing of confidential information with external users.

### 7. Educate Employees

Train employees to verify the scope of a sharing link before sending it to an external recipient.

---

# Why This Matters for Information Privacy

Information privacy depends not only on protecting systems from external attackers but also on ensuring that legitimate users cannot unnecessarily access or disclose information.

In this incident, the employee had legitimate access to the system, but the scope of that access was broader than necessary. Least privilege therefore acts as a preventative control against both intentional misuse and accidental disclosure.

---

# NIST SP 800-53 AC-6 Context

NIST SP 800-53 identifies **AC-6 — Least Privilege** as an access-control mechanism intended to limit authorized access to what users or processes need to accomplish assigned organizational tasks. AC-6 includes multiple enhancements that strengthen access restrictions and privilege management.

Relevant AC-6 enhancements include:

- **AC-6(1): Authorize Access to Security Functions**
- **AC-6(2): Non-Privileged Access for Nonsecurity Functions**
- **AC-6(4): Separate Processing Domains**
- **AC-6(5): Privileged Accounts**
- **AC-6(6): Privileged Access by Non-Organizational Users**
- **AC-6(7): Review of User Privileges**
- **AC-6(9): Log Use of Privileged Functions**
- **AC-6(10): Prohibit Non-Privileged Users from Executing Privileged Functions**

NIST's AC-6 family emphasizes limiting access to what is necessary for assigned tasks. Its user-privilege review enhancement calls for reviewing assigned privileges and removing or reassigning them when they are no longer appropriate.

---

# Security Improvements at a Glance

| Current Weakness | Improvement |
|---|---|
| Broad folder access | Role-based access |
| Temporary access remains active | Automatic expiration |
| Manual permission management | Automated access lifecycle |
| Sensitive and shareable content stored together | Separate resources by sensitivity |
| Limited permission review | Regular access audits |
| Accidental external sharing | External-sharing controls and employee training |

---

# Key Cybersecurity Concepts Demonstrated

- Principle of least privilege
- Information privacy
- Access control
- Role-based access control (RBAC)
- Temporary access
- Access expiration
- Permission reviews
- Data classification
- Confidential information protection
- Accidental disclosure risk
- External sharing controls
- NIST SP 800-53
- NIST AC-6
- Security control enhancements
- Secure data handling

---

# Portfolio Takeaway

This exercise demonstrates how a cybersecurity analyst can investigate a data leak, identify weaknesses in access management, map those weaknesses to a recognized security control, and recommend practical improvements. The incident highlights that effective information security requires not only technical controls but also appropriate authorization, controlled data sharing, periodic access reviews, and processes that reduce dependence on human memory.

---

## References

- NIST, **SP 800-53 — Security and Privacy Controls for Information Systems and Organizations**
- NIST CSRC, **Least Privilege — Computer Security Resource Center Glossary**
- NIST SP 800-53, **AC-6 — Least Privilege**
