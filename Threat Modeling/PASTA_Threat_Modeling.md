# PASTA Threat Modeling Assessment — Sneaker Marketplace Application

## Activity Overview

This assessment applies the Process of Attack Simulation and Threat Analysis (PASTA) framework to evaluate the security risks associated with a proposed mobile application for sneaker buyers and sellers.

The objective is to examine the application's business objectives, technical scope, potential threats, vulnerabilities, attack paths, and security controls before the application is launched.

---

## Scenario

The company is developing a mobile application for sneaker enthusiasts and collectors. The application will enable users to create accounts, buy and sell sneakers, communicate with sellers, rate sellers, and complete transactions using multiple payment options.

Because the application will process personal information and payment-related data, security must be incorporated into the application's design and development process.

---

# PASTA Stage I — Define Business Objectives

The following business objectives have been identified from the application requirements:

1. **Facilitate efficient buying and selling of sneakers** by connecting buyers and sellers and providing account-management and communication capabilities.
2. **Protect user privacy and personal information** so that users can have confidence in how their information is collected and handled.
3. **Provide secure and reliable payment processing** through multiple payment options while reducing the risk of payment-related issues and potential legal concerns.

---

# PASTA Stage II — Define the Technical Scope

## Technology Requirements

The application uses several technologies, including APIs, PKI, AES, RSA, SHA-256, and SQL.

SQL and the encryption technologies should receive particular security attention because the application will store and access sensitive user and transaction information. Improperly secured SQL interactions could expose the application to attacks such as SQL injection. Similarly, weaknesses in encryption implementation could expose sensitive information, including passwords or payment-related data. Protecting these components is therefore important to maintaining the confidentiality and integrity of application data.

---

# PASTA Stage III — Application Decomposition

The application will process information through several interconnected components. For example, a buyer may search the database for available sneakers, view seller information, communicate with the seller, and complete a purchase.

A simplified information flow is:

**User → Mobile Application → API → Database**

During a payment transaction, information may additionally flow through:

**User → Mobile Application → Payment Process → Database/Payment Service**

Because sensitive information may pass through multiple components, authentication, authorization, encryption, and secure database access should be applied throughout the data flow.

---

# PASTA Stage IV — Threat Analysis

Two potential threats to the sneaker marketplace application are identified below.

## 1. Phishing and Social Engineering

An attacker could attempt to deceive users or employees into disclosing login credentials or other sensitive information. Compromised credentials could subsequently be used to gain unauthorized access to user accounts or application resources.

## 2. Malicious Database Attacks

An attacker could attempt to exploit the application's database functionality by submitting malicious input through application fields. If input is not properly validated and handled, the attacker could potentially access or modify information without authorization.

---

# PASTA Stage V — Vulnerability Analysis

Two vulnerabilities that could potentially be exploited are:

## 1. SQL Injection

If user-provided input is incorporated directly into SQL queries without appropriate validation or parameterization, an attacker could manipulate database queries and potentially access, modify, or delete unauthorized information.

## 2. Inadequate Protection of Sensitive Data

If passwords, payment information, or other sensitive data are not adequately protected during storage or transmission, an attacker who obtains access to the information could potentially misuse it.

---

# PASTA Stage VI — Attack Analysis

The following examples illustrate how identified vulnerabilities could potentially be exploited.

### Potential Database Attack Path

```text
Attacker
   |
   v
Identify vulnerable application input
   |
   v
Submit malicious input
   |
   v
Exploit application vulnerability
   |
   v
Gain unauthorized database access
   |
   v
Read or modify sensitive information
```

### Potential Credential-Based Attack Path

```text
Attacker
   |
   v
Target user
   |
   v
Phishing / Social Engineering
   |
   v
Obtain user credentials
   |
   v
Authenticate as the compromised user
   |
   v
Access application resources
```

These attack paths demonstrate how weaknesses in application input handling or user authentication could provide an entry point to sensitive application information.

---

# PASTA Stage VII — Security Controls

The following four security controls can reduce the likelihood and potential impact of security incidents.

## 1. Input Validation and Parameterized Queries

Application input should be properly validated, and parameterized SQL queries should be used to reduce the risk of SQL injection attacks.

## 2. Encryption

Sensitive information should be protected using appropriate encryption mechanisms. The application specification identifies AES for protecting sensitive data and RSA for exchanging keys between the application and the user's device.

## 3. Multi-Factor Authentication

Multi-factor authentication should be implemented to provide an additional layer of protection if user credentials are compromised through phishing or other attacks.

## 4. Least Privilege and Access Controls

Users and application components should receive only the permissions required to perform their intended functions. Restricting database and application permissions can limit the amount of information accessible following an account or component compromise.

---

# Security Requirements Summary

| PASTA Stage | Key Finding |
|---|---|
| **Stage I — Business Objectives** | Efficient buying and selling, protection of user privacy, and secure payment processing |
| **Stage II — Technical Scope** | APIs, encryption, hashing, and SQL require security consideration |
| **Stage III — Application Decomposition** | Users, the mobile application, APIs, databases, and payment processes exchange sensitive information |
| **Stage IV — Threat Analysis** | Phishing/social engineering and malicious database attacks |
| **Stage V — Vulnerability Analysis** | SQL injection and inadequate protection of sensitive information |
| **Stage VI — Attack Analysis** | Attackers may exploit application input or compromised credentials |
| **Stage VII — Security Controls** | Input validation, encryption, MFA, and least privilege |

---

# Conclusion

Applying the PASTA framework provides a structured approach to evaluating the security of the proposed sneaker marketplace application. The application must support its business objectives while protecting personal and payment-related information. The primary risks identified include phishing and social engineering, malicious database attacks, SQL injection, and inadequate protection of sensitive data. Implementing input validation, encryption, multi-factor authentication, and least-privilege access controls can help reduce these risks before the application is launched.
