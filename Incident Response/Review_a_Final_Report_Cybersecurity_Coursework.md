# Review a Final Report — Incident Response Coursework

## Activity overview

**Role:** Level-one Security Operations Center (SOC) analyst  
**Incident type:** Customer data theft through an e-commerce web application vulnerability  
**Incident date:** December 28, 2022  
**Report status:** Incident closed following investigation

## Quiz answers

### Question 1: What type of security incident was the organization affected by?

**Answer: Data theft**

The attacker accessed customer personal identifiable information (PII) and financial information through a vulnerability in the e-commerce web application and collected customer data.

### Question 2: Which section of the report includes an explanation of the root cause of the incident?

**Answer: Investigation**

The Investigation section explains that a vulnerability in the e-commerce application allowed the attacker to access customer purchase-confirmation pages by modifying the order number in the URL.

### Question 3: What did the attacker use to exploit the e-commerce web application vulnerability?

**Answer: Forced browsing**

The attacker changed the order number in the URL string of a purchase-confirmation page to access other customers' purchase-confirmation pages and their data.

### Question 4: What recommendations did the organization implement to prevent future recurrences? Select two answers.

**Select:**
- **Implemented access control mechanisms**
- **Implemented routine vulnerability scans**

The report recommends routine vulnerability scans and penetration testing, along with access controls. These include allowlisting approved URLs and ensuring that only authenticated users can access protected content.

Identity-protection services were offered to affected customers as a response action; they are not one of the two future-prevention recommendations. The report does not say that the company paid the attacker's $50,000 demand.

## Incident handler's journal — review notes

### What happened?

An attacker exploited a vulnerability in the company's e-commerce web application to access customer purchase-confirmation pages. By modifying the order number in the URL, the attacker could view records associated with other orders and collect customer information. The report states that the exposed information included personal identifiable information (PII) and financial information.

### When did it happen?

- **December 22, 2022, approximately 3:13 p.m. PT:** An employee received an email from an external sender claiming customer data had been stolen and demanding $25,000 in cryptocurrency. The employee assumed it was spam and deleted it.
- **December 28, 2022, 7:20 p.m. PT:** The report identifies this as the time of the security incident. The same employee received another email from the sender, this time containing a sample of the stolen customer data and a demand for $50,000. The employee notified the security team.
- **December 28–31, 2022:** The security team investigated how the data was stolen and assessed the extent of the exposure. The team reviewed web server access logs and identified a high volume of sequential customer-order requests.

### What actions did the company take?

- The employee's report prompted the security team to investigate.
- The security team reviewed web server access logs to determine how the attacker accessed customer records and assess the scope of the incident.
- The organization worked with its public relations department to disclose the breach to affected customers.
- The organization offered free identity-protection services to affected customers.

### What was the root cause?

A vulnerability in the e-commerce web application allowed forced browsing. The application did not adequately prevent someone from changing an order number in a URL and viewing another customer's purchase-confirmation page. The logs showed an unusually high volume of sequentially listed customer orders, helping the team identify the activity.

### What did the report recommend?

- Perform routine vulnerability scans and penetration testing.
- Implement URL allowlisting so that requests outside the approved URL range are blocked.
- Require authentication before users can access protected content.

### Analyst's takeaway

As a developing cybersecurity analyst, I would focus on the importance of server-side authorization checks for every customer record. Knowing or changing an order number in a URL should never be sufficient to access another customer's information. Monitoring web logs for repeated sequential requests can also help identify suspicious access patterns. Vulnerability testing and access controls should be used together, rather than relying on monitoring alone.

## Source note

These notes are based on the course activity and the final-report text reproduced in the available course reference. The course introduction says the breach involved over one million users, while the report's executive summary says approximately 50,000 customer records were affected. I have retained the figure stated in the report when describing its findings; the discrepancy should be checked against the original course document if exact figures are required.
