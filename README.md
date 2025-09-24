# Phishing Email Analysis

## Task
This repository contains the deliverables for Task 2 of the Cyber Security Internship: analyzing phishing email samples and identifying phishing indicators.

## Contents
- `Phishing-Analysis.pdf` - Detailed analysis report (also available as PDF).
- `sample-email.txt` - Raw sample email including headers and HTML body (fabricated for training).
- `README.md` - This file.

## Summary
This project analyzes two phishing-style samples: a PayPal look-alike credential phish (with full headers provided) and a Microsoft-style scam example. The analysis covers:
- Header authentication checks (SPF/DKIM/DMARC)
- Originating IP and Message-ID checks
- Mismatched and look-alike URLs
- Social-engineering tactics such as urgency and fear
- Recommended remediation steps

## How to use
1. Review `sample-email.txt` for the raw headers and email HTML.
2. Open `Phishing-Analysis.pdf` for a concise analysis you can submit.


```
=== MXToolbox - Email Header Analyzer (simulated) ===

Received path:
  mail.example.com <- mailout.hosting-provider.info [198.51.100.45]

SPF Check:
  Result: FAIL
  Explanation: domain 'paypal-security.com' is not authorized to send from IP 198.51.100.45.
  Received-SPF: fail (domain of paypal.com does not designate 198.51.100.45 as permitted sender)

DKIM Check:
  Result: NONE
  Explanation: No DKIM signature found in the message headers (dkim=none).

DMARC Check:
  Result: FAIL
  Explanation: DMARC policy not met; alignment fails. (dmarc=fail)

Message-ID / Return-Path:
  Message-ID domain: mailout.hosting-provider.info
  Return-Path domain: paypal-security.com
  Note: Both differ from legitimate paypal.com mail servers.

Originating IP:
  IP: 198.51.100.45
  Lookup: Hosting provider / generic mail hosting (not registered to paypal.com)

Conclusion:
  Multiple authentication failures (SPF=fail, DKIM=none, DMARC=fail), inconsistent message-id/return-path, and originating IP belonging to a generic hosting provider strongly indicate a forged/suspicious email (phishing).
```
