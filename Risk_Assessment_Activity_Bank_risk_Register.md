# Cybersecurity Risk Assessment — Bank Funds Risk Register

> **Cybersecurity Portfolio Project**  
> **Framework Context:** NIST Cybersecurity Framework (CSF)  
> **Category:** Risk Assessment | Risk Management | Financial Security  
> **Skills Demonstrated:** Risk identification, likelihood assessment, impact assessment, risk scoring, prioritization, risk register development

---

## Project Description

As a security professional on a cybersecurity team at a commercial bank, I performed a risk assessment focused on threats to the bank's funds and business operations. I evaluated five common risks by considering the bank's operational environment, estimating the likelihood and severity of each risk, and calculating an overall priority score. The assessment demonstrates how a security team can use a risk register to prioritize limited security resources.

---

## Operational Environment

The bank operates in a coastal area with low crime rates and has:

- **100 on-premises employees**
- **20 remote employees**
- **2,000 individual customer accounts**
- **200 commercial customer accounts**
- Services marketed by a professional sports team and **10 local businesses**
- Strict financial regulations requiring the bank to protect customer data and funds
- Daily requirements to maintain sufficient cash reserves to meet Federal Reserve requirements

The environment contains multiple people, systems, accounts, third-party relationships, and physical locations that could introduce security risks.

---

## Risk Factors — Notes

Security events can affect the bank's funds through social engineering, compromised employee or customer data, unauthorized disclosure of financial records, physical theft, and third-party or supply-chain disruptions. The bank's remote workforce, large customer base, regulatory requirements, coastal location, and reliance on external partners create opportunities for both cyber and physical threats to disrupt operations or cause financial loss.

---

## Risk Assessment Methodology

The assessment uses the following formula:

```text
Likelihood × Severity = Priority
```

Both **Likelihood** and **Severity** are scored from 1 to 3.

### Likelihood

| Score | Rating | Meaning |
|------:|--------|---------|
| 1 | Low | Low chance of occurring |
| 2 | Moderate | Moderate chance of occurring |
| 3 | High | High chance of occurring |

### Severity

| Score | Rating | Meaning |
|------:|--------|---------|
| 1 | Low | Limited impact on the organization |
| 2 | Moderate | Significant but manageable impact |
| 3 | High | Major impact to finances, operations, data, compliance, or reputation |

### Priority

```text
Priority = Likelihood × Severity
```

A higher score indicates that the security team should generally prioritize the risk more urgently.

---

## Risk Register

| Risk | Likelihood | Severity | Priority | Priority Level |
|------|-----------:|---------:|---------:|----------------|
| Business Email Compromise | 3 | 3 | **9** | High |
| Compromised User Database | 2 | 3 | **6** | High |
| Financial Records Leak | 2 | 3 | **6** | High |
| Theft | 1 | 3 | **3** | Moderate |
| Supply Chain Attack | 1 | 3 | **3** | Moderate |

---

## 1. Business Email Compromise

**Likelihood: 3 — High**

The bank has 120 employees, including 20 remote employees, creating a relatively large user population that may be targeted through phishing and social engineering. Business email compromise is a common attack method because attackers can use compromised accounts to impersonate employees, request fraudulent payments, or obtain sensitive information.

**Severity: 3 — High**

A successful business email compromise could directly affect the bank's funds through fraudulent transfers or payment instructions. It could also expose sensitive information, damage customer trust, and create regulatory and reputational consequences.

**Priority:**

```text
3 × 3 = 9
```

**Priority Score: 9 — High**

### Recommended Focus

This risk should receive the highest priority. Appropriate controls include phishing-resistant authentication where feasible, multifactor authentication, email security controls, employee security awareness training, payment verification procedures, and monitoring for suspicious account activity.

---

## 2. Compromised User Database

**Likelihood: 2 — Moderate**

The bank maintains information associated with 2,000 individual accounts and 200 commercial accounts. A database containing a large amount of customer information is an attractive target for attackers, although strong access controls and security monitoring can reduce the likelihood of compromise.

**Severity: 3 — High**

A compromised user database could expose sensitive customer information and potentially enable account takeover, fraud, or other financial crimes. The bank could also face regulatory penalties, investigation costs, customer losses, and reputational damage.

**Priority:**

```text
2 × 3 = 6
```

**Priority Score: 6 — High**

### Recommended Focus

The bank should prioritize strong database access controls, least-privilege permissions, encryption, monitoring, secure backups, vulnerability management, and regular access reviews.

---

## 3. Financial Records Leak

**Likelihood: 2 — Moderate**

The bank handles sensitive financial records across many employees, systems, and business processes. The combination of a large customer base and multiple users with access creates opportunities for accidental disclosure, compromised credentials, or unauthorized access.

**Severity: 3 — High**

A financial records leak could expose sensitive customer and business information. Because the bank operates under strict financial regulations, a significant breach could result in regulatory penalties, legal costs, customer loss, financial harm, and substantial reputational damage.

**Priority:**

```text
2 × 3 = 6
```

**Priority Score: 6 — High**

### Recommended Focus

Security resources should include data loss prevention, encryption, access controls, audit logging, employee training, secure data handling procedures, and regular reviews of access to sensitive financial information.

---

## 4. Theft

**Likelihood: 1 — Low**

The bank is located in an area with low crime rates, which reduces the likelihood of physical theft. However, physical theft cannot be completely eliminated because funds, equipment, documents, and other valuable assets may still be targeted.

**Severity: 3 — High**

A theft involving bank funds could cause direct financial losses and potentially disrupt operations. Depending on the circumstances, theft could also create regulatory, legal, and reputational consequences.

**Priority:**

```text
1 × 3 = 3
```

**Priority Score: 3 — Moderate**

### Recommended Focus

Physical security controls should still be maintained, including access restrictions, surveillance, secure storage, inventory controls, visitor management, and procedures for protecting cash and sensitive equipment.

---

## 5. Supply Chain Attack

**Likelihood: 1 — Low**

A supply chain attack is possible because the bank relies on external vendors, services, and business relationships. The coastal location also creates potential for environmental disruptions that could affect suppliers and the availability of critical resources, although a targeted supply chain cyberattack may be less frequent than common user-focused attacks.

**Severity: 3 — High**

A successful supply chain compromise could affect critical systems or services and potentially disrupt the bank's ability to operate. Disruption to financial services or resources needed to meet daily requirements could cause significant financial, regulatory, and reputational consequences.

**Priority:**

```text
1 × 3 = 3
```

**Priority Score: 3 — Moderate**

### Recommended Focus

The bank should maintain vendor risk assessments, third-party security requirements, business continuity plans, supplier monitoring, backup procedures, and contingency plans for critical services.

---

## Risk Prioritization

| Rank | Risk | Score | Priority |
|-----:|------|------:|----------|
| 1 | Business Email Compromise | **9** | Highest |
| 2 | Compromised User Database | **6** | High |
| 2 | Financial Records Leak | **6** | High |
| 4 | Theft | **3** | Moderate |
| 4 | Supply Chain Attack | **3** | Moderate |

### Interpretation

**Business Email Compromise** receives the highest priority score because it has both a high likelihood and a high potential impact. The compromised user database and financial records leak have lower likelihood scores but remain high-priority risks because their potential impact on customer information, finances, regulatory compliance, and reputation is severe.

Theft and supply chain attacks receive lower overall scores in this assessment because their estimated likelihood is lower. However, their high potential severity means they should still have appropriate preventive and contingency controls.

---

## Risk Matrix

| Likelihood \ Severity | 1 — Low | 2 — Moderate | 3 — High |
|-------------------------|---------:|--------------:|---------:|
| **3 — High** | 3 | 6 | **9** |
| **2 — Moderate** | 2 | 4 | **6** |
| **1 — Low** | 1 | 2 | **3** |

The matrix shows why a risk with a lower likelihood can still require attention when its potential impact is high.

---

## Connection to the NIST Cybersecurity Framework

Risk assessment supports the **Identify** function of the NIST Cybersecurity Framework. Identifying assets, threats, vulnerabilities, and organizational risks helps security teams understand where the greatest exposure exists.

This assessment demonstrates the process of:

```text
Identify Risks
      ↓
Estimate Likelihood
      ↓
Estimate Impact / Severity
      ↓
Calculate Risk
      ↓
Prioritize Resources
      ↓
Select Appropriate Controls
```

The risk register provides a structured way to communicate these decisions and focus security resources on the most significant threats.

---

## Key Cybersecurity Concepts Demonstrated

- Risk assessment
- Risk registers
- Risk identification
- Likelihood analysis
- Impact/severity analysis
- Risk prioritization
- Risk scoring
- Financial-sector cybersecurity
- Business email compromise
- Data compromise
- Data leakage
- Physical security
- Supply chain risk
- Regulatory risk
- Security resource prioritization
- NIST Cybersecurity Framework

---

## Final Summary

In this assessment, I evaluated five risks affecting a commercial bank's funds and operational environment: business email compromise, compromised user databases, financial records leaks, theft, and supply chain attacks. I assigned likelihood and severity scores based on the organization's environment and calculated priority scores using the formula `Likelihood × Severity = Risk`. The results identified business email compromise as the highest-priority risk, while database compromise and financial records leaks also require significant security attention. This exercise demonstrates how a cybersecurity team can use structured risk assessment to prioritize security resources and support informed risk-management decisions.
