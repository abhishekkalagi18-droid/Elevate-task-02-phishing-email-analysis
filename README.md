# Task 02 — Phishing Email Analysis

## 1. Problem Statement

Phishing is one of the most common social-engineering attacks used to trick people into revealing sensitive information, clicking malicious links, opening dangerous attachments, or performing unauthorized actions.

In this task, a simulated phishing email is analyzed to understand how attackers make fraudulent emails appear legitimate and how suspicious characteristics can be identified.

The analysis focuses on:

* Sender email address
* Subject line
* Email body
* Suspicious links
* Social-engineering techniques
* Urgent or threatening language
* Attachments
* Email headers
* Grammar and formatting
* Overall phishing indicators

> **Safety:** The examples in this document are simulated training examples. Suspicious links and attachments should not be opened on a real system.

---

# 2. Objective

The objectives of this task are to:

1. Understand the concept of phishing.
2. Identify common phishing characteristics.
3. Analyze a suspicious sender address.
4. Examine suspicious URLs.
5. Understand basic email-header analysis.
6. Identify social-engineering techniques.
7. Recognize urgency and threatening language.
8. Document evidence in a structured security report.
9. Develop practical email-threat-analysis skills.

---

# 3. What is Phishing?

**Phishing** is a social-engineering attack in which an attacker impersonates a trusted person, company, or service to deceive a victim.

The attacker normally sends a fraudulent message through:

* Email
* SMS
* Social media
* Messaging applications
* Fake websites
* Collaboration platforms

The objective may be to steal:

* Usernames
* Passwords
* OTPs
* Banking information
* Credit-card information
* Personal information
* Company credentials

Phishing can also be used to distribute malware or convince victims to transfer money.

### Simple Example

An attacker creates an email that appears to come from a bank:

```text
From: Bank Security <security@bank-security-example.com>

Subject: Urgent: Your account will be suspended

Dear Customer,

We detected suspicious activity on your account.

Verify your account within 24 hours:

https://fake-bank-login.example/verify

Failure to verify will result in account suspension.
```

A victim may believe the email is from the bank and click the link.

The fake website may then request:

```text
Username:
Password:
OTP:
```

The attacker can potentially collect these credentials.

---

# 4. How a Phishing Attack Works

A typical phishing attack follows this sequence:

```text
Attacker
   |
   v
Creates fraudulent message
   |
   v
Impersonates trusted organization
   |
   v
Sends message to victim
   |
   v
Victim receives email
   |
   v
Victim trusts the message
   |
   v
Clicks link / opens attachment
   |
   v
Fake website or malware
   |
   v
Sensitive information compromised
```

The important point is that phishing frequently attacks **human trust and decision-making**, rather than directly exploiting a technical vulnerability.

---

# 5. Common Types of Phishing

## 5.1 Email Phishing

Large numbers of fraudulent emails are sent to potential victims.

Example:

```text
Your account has been suspended.
Click here to restore access.
```

---

## 5.2 Spear Phishing

A targeted phishing attack directed at a specific individual or organization.

Example:

```text
Hi Rahul,

Please review the attached invoice before today's meeting.

Regards,
Finance Department
```

The attacker may research the victim beforehand to make the message more convincing.

---

## 5.3 Whaling

A phishing attack targeting senior executives or high-value individuals.

Examples of targets:

* CEO
* CFO
* IT administrator
* Company director

The attacker may attempt to convince an employee to transfer money or disclose confidential information.

---

## 5.4 Smishing

Phishing performed through SMS or text messages.

Example:

```text
Your parcel could not be delivered.

Update your address:
https://fake-delivery.example
```

---

## 5.5 Vishing

Phishing performed through voice calls.

An attacker may pretend to be:

* Bank employee
* Technical-support representative
* Government official
* Company administrator

---

## 5.6 Clone Phishing

The attacker creates a copy of a legitimate email and replaces the original link or attachment with a malicious one.

---

# 6. Anatomy of a Phishing Email

A phishing email can be divided into several components:

```text
+------------------------------------------+
| From: suspicious@example-domain.com      |
| Subject: URGENT: Account Verification    |
+------------------------------------------+
|                                          |
| Dear Customer,                           |
|                                          |
| We detected unusual activity.            |
|                                          |
| Verify your account immediately.         |
|                                          |
| [ VERIFY ACCOUNT ]                       |
|                                          |
| Your account may be suspended.           |
|                                          |
| Regards,                                 |
| Security Team                            |
+------------------------------------------+
```

Each section can contain indicators.

---

# 7. Phishing Indicator 1 — Suspicious Sender

The sender address is one of the first things that should be checked.

### Example

```text
Amazon Support <customer-service@amazon-orders.net>
```

The email claims to be from Amazon, but the domain is:

```text
amazon-orders.net
```

This should raise suspicion because the sender domain does not match the organization being impersonated.

### What to check

Look at:

```text
From:
Reply-To:
Return-Path:
```

A suspicious situation could be:

```text
From: bank-support@example.net
Reply-To: attacker@example.org
```

A different `Reply-To` address does not automatically prove phishing, but it is worth investigating.

---

# 8. Phishing Indicator 2 — Urgent Subject

Attackers frequently create urgency.

Examples:

```text
URGENT: Your account will be closed
```

```text
ACTION REQUIRED: Verify your identity
```

```text
FINAL WARNING: Payment required
```

The purpose is to make the victim act quickly instead of carefully examining the email.

### Important Principle

**Urgency does not prove phishing.**

Legitimate organizations can also send urgent messages.

However, urgency combined with suspicious links, sender inconsistencies, or credential requests becomes a stronger warning sign.

---

# 9. Phishing Indicator 3 — Generic Greeting

A phishing email may use:

```text
Dear Customer
```

```text
Dear User
```

```text
Hello Sir/Madam
```

instead of identifying the recipient.

This can happen because attackers send the same message to thousands of people.

However, a generic greeting is **not proof of phishing** by itself.

---

# 10. Phishing Indicator 4 — Suspicious Activity Claims

Attackers often create a fake security problem.

Example:

```text
We detected unusual login activity on your account.
```

Other examples:

```text
Someone attempted to access your account.
```

```text
A suspicious transaction was detected.
```

```text
Your password has expired.
```

The objective is to create fear and convince the victim to follow the attacker's instructions.

---

# 11. Phishing Indicator 5 — Threatening Language

A phishing email may threaten the victim with consequences.

Example:

```text
Your account will be suspended within 24 hours.
```

Another example:

```text
Failure to verify your account will result in permanent closure.
```

These statements attempt to create pressure.

A security analyst should separate:

**Claim**

from

**Evidence**

For example:

```text
Claim:
Your account will be suspended.

Evidence:
The email provides no legitimate account identifier
and links to an unrelated domain.
```

---

# 12. Phishing Indicator 6 — Suspicious URL

Links require careful examination.

Example:

```text
Displayed text:

Verify Your Account
```

The actual destination may be:

```text
https://secure-account-verification.example/login
```

The displayed text can look legitimate while the actual destination belongs to another domain.

### URL Analysis

Consider:

```text
https://login.example.com
```

versus:

```text
https://example.com.attacker.example
```

The second URL belongs to:

```text
attacker.example
```

not:

```text
example.com
```

### Important

Never click a suspicious link just to investigate it.

Use safe analysis methods such as examining the URL text or using an isolated security-analysis environment.

---

# 13. Phishing Indicator 7 — Credential Requests

A particularly important warning sign is an unexpected request for sensitive information.

Examples:

```text
Enter your password.
```

```text
Enter your OTP.
```

```text
Confirm your banking PIN.
```

```text
Upload your identity document.
```

Unexpected requests for credentials should be treated cautiously.

---

# 14. Phishing Indicator 8 — Suspicious Attachments

Phishing emails can contain attachments such as:

```text
Invoice.pdf
Payment_Details.xlsx
Account_Verification.doc
Security_Update.zip
```

An attachment should not be trusted simply because its filename looks legitimate.

Potential risks include:

* Malware
* Credential-stealing files
* Malicious macros
* Exploit documents
* Script files

Do not open unexpected attachments on your normal computer.

---

# 15. Phishing Indicator 9 — Grammar and Formatting

Some phishing emails contain:

* Spelling mistakes
* Grammar errors
* Strange capitalization
* Poor formatting
* Inconsistent fonts
* Unusual punctuation
* Incorrect company terminology

Example:

```text
Your Account has been suspanded!!!
Please verifiy immediatly.
```

However, modern phishing campaigns can use professionally written content, including AI-generated text.

Therefore:

**Good grammar does not mean an email is legitimate.**

---

# 16. Email Header Analysis

Email headers contain technical information about how an email was transmitted.

Important fields include:

```text
From:
To:
Date:
Subject:
Reply-To:
Return-Path:
Received:
Authentication-Results:
```

Authentication mechanisms commonly encountered include:

```text
SPF
DKIM
DMARC
```

---

# 17. SPF

**SPF = Sender Policy Framework**

SPF helps a receiving mail system determine whether a sending server is authorized to send mail for a domain.

Example:

```text
spf=pass
```

or:

```text
spf=fail
```

An SPF failure can be an indicator that requires investigation.

However:

**SPF failure alone does not automatically prove that an email is phishing.**

---

# 18. DKIM

**DKIM = DomainKeys Identified Mail**

DKIM uses cryptographic signatures to help verify that an email was authorized by the signing domain and was not altered after signing.

Example:

```text
dkim=pass
```

or:

```text
dkim=fail
```

A failed DKIM check can be suspicious, but context is important.

---

# 19. DMARC

**DMARC = Domain-based Message Authentication, Reporting and Conformance**

DMARC builds on SPF and DKIM and helps domain owners specify how receiving systems should handle messages that fail authentication/alignment checks.

Example:

```text
dmarc=pass
```

or:

```text
dmarc=fail
```

Authentication results should be interpreted together with the sender domain, message content, and other evidence.

---

# 20. Practical Example 1 — Fake Amazon Email

### Simulated Email

```text
From:
Amazon Support <customer-service@amazon-orders.net>

Subject:
Your Amazon Order Has Been Cancelled

Dear Customer,

We were unable to process your recent order due to an
issue with your payment method.

If you do not update your payment information within
24 hours, your account will be suspended.

[ Update Payment Method ]

https://amazon-secure-payment.example/login

Thank you,
Amazon Support Team
```

### Analysis

| Evidence      | Observation                                    |
| ------------- | ---------------------------------------------- |
| Sender        | Domain does not match the claimed organization |
| Subject       | Creates urgency                                |
| Greeting      | Generic                                        |
| Payment claim | No specific order information                  |
| Deadline      | 24-hour pressure                               |
| Link          | Unrelated domain                               |
| Threat        | Account suspension                             |
| Signature     | Generic                                        |

### Conclusion

This simulated email contains multiple phishing indicators. The combination of sender-domain inconsistency, urgency, generic content, threatening language, and a suspicious URL makes it unsafe to trust without independent verification.

---

# 21. Practical Example 2 — Fake DHL Delivery Email

### Simulated Email

```text
From:
DHL Express <notifications@dhl-tracking.info>

Subject:
Action Required: Your Package Is On Hold

Hello,

Your package could not be delivered because your
address information is incomplete.

Please confirm your address within 48 hours:

[ Confirm Your Address ]

https://dhl-delivery-update.example/confirm

Regards,
DHL Express
```

### Analysis

Suspicious characteristics:

1. Sender domain does not match the claimed company.
2. Subject creates urgency.
3. Generic greeting.
4. Delivery problem is not independently verified.
5. 48-hour deadline creates pressure.
6. Link points to an unrelated domain.
7. No reliable contact or tracking information is provided.

---

# 22. Practical Example 3 — Fake Microsoft Security Email

```text
From:
Microsoft Security <security@microsoft-alert.example>

Subject:
URGENT: Your Microsoft Account Will Be Suspended

Dear User,

We detected unusual activity on your Microsoft account.

Your account will be permanently suspended within 24 hours
unless you verify your identity immediately.

Verify your account:

https://microsoft-security-verification.example/verify

If you do not complete the verification, your account and
associated files will be permanently deleted.

Microsoft Security Team
```

### Indicators

```text
1. Suspicious sender domain
2. Urgent subject
3. Generic greeting
4. Unusual activity claim
5. Short deadline
6. Threat of suspension
7. Suspicious verification URL
8. Threat of data deletion
9. Generic signature
```

---

# 23. Social Engineering in Phishing

Phishing primarily exploits human psychology.

Common techniques include:

### Fear

```text
Your account will be deleted.
```

### Urgency

```text
Respond within 2 hours.
```

### Authority

```text
IT Security Department
```

### Curiosity

```text
Someone viewed your private photos.
```

### Financial motivation

```text
You have received ₹50,000.
```

### Trust

Attackers impersonate:

* Banks
* Universities
* Delivery companies
* Cloud services
* Government organizations
* Employers
* Friends or colleagues

---

# 24. How to Analyze a Phishing Email

Use this workflow:

```text
              START
                |
                v
        Examine sender
                |
                v
       Check subject line
                |
                v
      Read email carefully
                |
                v
       Inspect URLs safely
                |
                v
       Check attachments
                |
                v
       Examine headers
                |
                v
    Check SPF/DKIM/DMARC
                |
                v
   Identify social engineering
                |
                v
      Document evidence
                |
                v
             REPORT
```

---

# 25. Phishing Analysis Checklist

```text
[ ] Sender domain checked
[ ] Reply-To checked
[ ] Return-Path checked
[ ] Subject analyzed
[ ] Generic greeting identified
[ ] Urgency checked
[ ] Threatening language checked
[ ] URL analyzed safely
[ ] Displayed URL compared with destination
[ ] Attachments identified
[ ] SPF checked
[ ] DKIM checked
[ ] DMARC checked
[ ] Social-engineering techniques identified
[ ] Grammar/formatting examined
[ ] Evidence documented
```

---

# 26. Recommended Response to a Suspected Phishing Email

If an email appears suspicious:

1. Do not click links.
2. Do not open unexpected attachments.
3. Do not enter credentials.
4. Do not reply to the attacker.
5. Verify the request through an independent channel.
6. Report the email to the organization's security team.
7. Follow the organization's phishing-reporting procedure.
8. Delete or quarantine the message according to policy.

If credentials were already entered, immediately follow the organization's incident-response procedure and change affected credentials through the legitimate service.

---

# 27. Tools Used for Learning

Possible tools include:

* Email client
* Text editor
* Raw email-header viewer
* Free email-header analysis services
* Browser URL inspection
* Cybersecurity lab environment

For this task, avoid paid tools. The objective is to understand the **analysis methodology**, not to purchase software.

---

# 28. Evidence to Include in GitHub

Recommended evidence:

```text
screenshots/
├── sender-analysis.png
├── suspicious-url.png
├── header-analysis.png
└── phishing-indicators.png
```

Remove real personal information before uploading screenshots.

Never upload:

* Real passwords
* OTPs
* Private email addresses
* Session tokens
* Authentication cookies
* Confidential company information

---

# 29. Final Findings

The simulated phishing examples demonstrate that phishing emails commonly combine multiple techniques rather than relying on a single indicator.

Important indicators include:

* Suspicious sender domains
* Impersonation
* Urgent requests
* Threatening language
* Generic greetings
* Suspicious URLs
* Credential requests
* Unexpected attachments
* Authentication anomalies
* Social-engineering techniques

A professional analyst should avoid declaring an email malicious based on only one weak indicator. Instead, multiple pieces of evidence should be collected and evaluated together.

---

# 30. Conclusion

This task demonstrated the process of analyzing a phishing email from both a **human-behavior perspective** and a **technical perspective**.

The human side involves identifying manipulation techniques such as urgency, fear, authority, and trust.

The technical side involves examining sender addresses, URLs, headers, and authentication results such as SPF, DKIM, and DMARC.

The most important lesson is:

> **Do not trust an email simply because it looks professional. Verify the sender, destination, request, and supporting evidence independently.**

This analysis provides a foundation for further cybersecurity activities such as email threat detection, SOC analysis, incident response, and security awareness.
