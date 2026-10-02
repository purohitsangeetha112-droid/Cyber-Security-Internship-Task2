# Cyber Security Internship — Task 2
## Phishing Email Analysis

**Author:** Sangu  
**Date:** October 2, 2026  
**Platform:** Kali Linux  
**Tools:** Text Editor, Manual Header Analysis

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Objective](#2-objective)
3. [Methodology — What I Did](#3-methodology--what-i-did)
4. [Phishing Indicators Found](#4-phishing-indicators-found)
5. [Email Header Analysis](#5-email-header-analysis)
6. [Risk Assessment](#6-risk-assessment)
7. [What I Learned](#7-what-i-learned)
8. [Interview Questions & Answers](#8-interview-questions--answers)
9. [Tools & Technologies Used](#9-tools--technologies-used)
10. [Conclusion](#10-conclusion)

---

## 1. Executive Summary

This report documents the analysis of a phishing email sample designed to impersonate a bank's security team. The objective was to identify phishing characteristics, including spoofed sender addresses, mismatched URLs, urgent language, and header discrepancies. The analysis revealed multiple red flags consistent with a credential-harvesting attack.

---

## 2. Objective

To identify phishing characteristics in a suspicious email sample and understand the tactics used by attackers to deceive victims.

---

## 3. Methodology — What I Did

1. Obtained a sample phishing email and saved it as sample.eml.
2. Examined the sender's email address and Reply-To field for spoofing.
3. Inspected the email headers for SPF, DKIM, and DMARC authentication results.
4. Identified suspicious links by comparing visible text against the actual href destination.
5. Looked for urgent or threatening language in the email body.
6. Checked for generic greetings and requests for sensitive information.
7. Summarized phishing traits found in the email for this report.

---

## 4. Phishing Indicators Found

| # | Indicator | Observation | Risk |
|---|-----------|-------------|------|
| 1 | Spoofed Sender Address | From: security@your-bank-alert.com — not a real bank domain | High |
| 2 | Reply-To Mismatch | Reply-To points to verify-account@secure-bank-verify.ru (.ru domain) | High |
| 3 | Return-Path Mismatch | Return-Path is bounce@mailchimp.com — not the bank | High |
| 4 | Mismatched URL | Visible: https://www.yourbank.com/verify-account — Actual: http://your-bank-alert.com.secure-verify-login.ru/account/verify | High |
| 5 | Urgent Language | "verify your identity immediately" and "within 24 hours, your account will be permanently closed" | High |
| 6 | Financial Threat | "any remaining funds may be forfeited" | High |
| 7 | Generic Greeting | "Dear Valued Customer" instead of the recipient's real name | Medium |
| 8 | Requests Credentials | Asks for account number, password, and PIN — banks never ask this via email | High |
| 9 | Misleading Authentication | SPF/DKIM/DMARC pass for mailchimp.com, not for the claimed bank domain | High |

---

## 5. Email Header Analysis

| Header Field | Value | Analysis |
|--------------|-------|----------|
| From | security@your-bank-alert.com | Look-alike domain; not a real bank |
| Reply-To | verify-account@secure-bank-verify.ru | Foreign .ru domain — suspicious |
| Return-Path | bounce@mailchimp.com | Bulk mailer used to send the phishing email |
| Subject | URGENT: Your Account Has Been Suspended - Verify Now | Uses fear and urgency |
| SPF | Pass (mailchimp.com) | Passed for the wrong domain |
| DKIM | Pass (mailchimp.com) | Passed for the wrong domain |
| DMARC | Pass (mailchimp.com) | Passed for the wrong domain |
| Received from | mail-sor-f41.google.com [209.85.220.41] | Google relay; hides real origin |

**Key Insight:** SPF, DKIM, and DMARC all pass — but for mailchimp.com, not for the bank. Attackers abuse legitimate bulk-mail services to bypass authentication checks.

---

## 6. Risk Assessment

**Overall Risk Level: HIGH**

This email exhibits all the classic signs of a credential-harvesting phishing attack:
- Sender, Reply-To, and Return-Path point to three different domains.
- The link uses URL masking to hide a Russian destination behind a trusted-looking text.
- The email uses urgent and threatening language to pressure the victim.
- It requests account number, password, and PIN — information a bank would never ask for via email.
- Authentication checks pass for the wrong domain, showing why SPF/DKIM/DMARC alone are not sufficient.

**Recommendation:**
- Do not click any links or enter credentials.
- Report the email to IT/security and the bank.
- Delete the email immediately.
- If credentials were entered, change passwords and enable MFA right away.

---

## 7. What I Learned

Through this task, I gained practical experience in:

- Phishing Identification: Recognizing red flags like spoofed domains, urgent language, and generic greetings.
- Email Header Analysis: Understanding SPF, DKIM, DMARC, and why passing authentication does not guarantee legitimacy.
- URL Inspection: Using hover techniques to reveal real destinations hidden behind friendly anchor text.
- Social Engineering Tactics: How attackers exploit fear, urgency, and authority to manipulate victims.
- Incident Response: Steps to take when a phishing email is received — do not click, report, delete.
- Documentation Skills: Writing a professional phishing analysis report.

---

## 8. Interview Questions & Answers

**1. What is phishing?**  
Phishing is a cyberattack where attackers impersonate a trustworthy entity via email, text, or phone to trick victims into revealing sensitive information or installing malware.

**2. How to identify a phishing email?**  
Look for spoofed sender addresses, urgent or threatening language, generic greetings, spelling errors, mismatched URLs, suspicious attachments, and requests for personal information.

**3. What is email spoofing?**  
Email spoofing is the creation of an email with a forged sender address so it appears to come from a legitimate source.

**4. Why are phishing emails dangerous?**  
They lead to credential theft, financial loss, malware infections, ransomware, and unauthorized access. They are a primary initial attack vector in major breaches.

**5. How can you verify the sender's authenticity?**  
Check SPF, DKIM, and DMARC alignment in headers, verify the domain matches the official one, and contact the organization using a known number — never the reply-to in the email.

**6. What tools can analyze email headers?**  
MXToolbox, Google Admin Toolbox (Messageheader), Microsoft Message Header Analyzer, and Mailheader.org.

**7. What actions should be taken on suspected phishing emails?**  
Do not click links or open attachments. Report to IT/security, delete the email, and if you already interacted, change passwords and enable MFA immediately.

**8. How do attackers use social engineering in phishing?**  
They exploit human emotions — urgency, fear, curiosity, authority, greed — to trick victims into bypassing security. Examples include fake invoices, account suspension warnings, and prize notifications.

---

## 9. Tools & Technologies Used

- Manual email header inspection (text editor)
- Sample phishing email (sample.eml)
- Kali Linux
- Git & GitHub — version control and documentation

---

## 10. Conclusion

This task provided hands-on experience in phishing email analysis — a critical cybersecurity skill. By examining a suspicious email sample, I identified multiple phishing indicators including spoofed sender addresses, mismatched URLs, header discrepancies, and social engineering tactics. The exercise reinforced the importance of user awareness, email authentication protocols, and rapid incident response.

**Key Takeaway:**  
Phishing relies on human error, not technical exploits. Awareness and verification are the strongest defenses.

---

*End of Report*

EVIDENCE
<img width="1920" height="922" alt="VirtualBox_kali-linux-2026 1-virtualbox-amd64_02_10_2026_21_20_28" src="https://github.com/user-attachments/assets/a4c78900-a555-4d2a-ab15-869ddd874c75" />
