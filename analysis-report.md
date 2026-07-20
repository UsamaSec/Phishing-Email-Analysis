# Phishing Email Analysis Report

## Summary
This report analyzes a self-constructed phishing email impersonating internal IT support, requesting an urgent password reset. Header analysis confirmed sender spoofing and complete authentication failure (SPF, DKIM, and DMARC all failed), consistent with a credential-harvesting phishing attempt.

## Email Overview
| Field | Value |
|-------|-------|
| Claimed sender | it-support@example-corp.com |
| Subject line | URGENT: Your Password Will Expire in 24 Hours - Action Required |
| Date received | Mon, 20 Jul 2026 03:14:20 -0700 |
| Delivered to | usama.aslam@example-corp.com (test inbox) |

## Note on Sample Domain
`example-corp.com` is a fictional domain used for this exercise and does not resolve to real DNS records, confirmed via MXToolbox below.

![Confirmation that example-corp.com is not a registered domain](screenshots/example-corp-dns-notfound.png)


## Red Flags Identified (Content-Level)
- [x] Urgency/pressure language — subject line and body repeatedly stress a 24-hour deadline and threaten account suspension
- [x] Generic greeting — addressed to "Dear User" rather than the recipient's actual name
- [x] Suspicious/mismatched sender domain — visible "From" address appears legitimate, but Return-Path and Reply-To both point to a misspelled lookalike domain (it-suport-example-corp.com)
- [x] Embedded link with display text differing from actual URL — link text reads "Reset My Password Now" but the underlying URL points to an unrelated domain (verify-account-portal.net)
- [x] Request for credential action framed as urgent/mandatory
- [x] Internally contradictory logic — the email claims both that immediate action is required and that "no action is required," a common inconsistency in hastily constructed phishing templates


## Header Analysis

**Claimed "From" address:** [address]

**Actual sending server / Return-Path:** [what the raw headers show]

**Key header fields reviewed:**
```
[Paste relevant raw header snippet here - Received, Return-Path, Reply-To, etc.]
```

![Raw header view](screenshots/raw-headers.png)

## Authentication Results (SPF / DKIM / DMARC)

| Check | Result | What It Means |
|-------|--------|----------------|
| SPF | [Pass/Fail/None] | [1 sentence] |
| DKIM | [Pass/Fail/None] | [1 sentence] |
| DMARC | [Pass/Fail/None] | [1 sentence] |

![MXToolbox authentication results](screenshots/mxtoolbox-comparison.png)

## IOC Extraction

| Indicator | Type | VirusTotal Result |
|-----------|------|--------------------|
| example-corp-secure-login.verify-account-portal.net | Domain | 0/91 vendors flagged (Unrated) — fictional domain, no real-world reputation history |
| 185.220.101.47 | Originating IP (from Received header) | **13/91 vendors flagged as malicious**, including specific "Phishing" categorization from BitDefender and SOCRadar. Identified as a known Tor exit node (AS 60729, Stiftung Erneuerbare Freiheit). |

**Note:** While the sender domain was fictional for this exercise, the originating IP address used in the sample's Received header is a real, currently-flagged malicious address associated with phishing activity and Tor exit node infrastructure — reinforcing a realistic detail: attackers frequently route phishing traffic through Tor or other anonymizing infrastructure to obscure their true origin.

![VirusTotal IP lookup showing 13/91 malicious detections and Tor exit node tagging](screenshots/virustotal-ip-result.png)


## Verdict
**Phishing confirmed.** This email exhibits multiple independent indicators of a credential-harvesting phishing attempt: complete SPF/DKIM/DMARC authentication failure, a spoofed display sender masking a lookalike Return-Path/Reply-To domain, urgency-based social engineering language, a mismatched embedded link, and an originating IP address independently flagged by 13 security vendors as malicious with a specific phishing classification. The convergence of header-level, content-level, and reputation-based evidence provides high confidence this is a phishing attempt.

## Recommendation
[What should happen next in a real environment - e.g., block sender domain, report to email provider, user awareness reminder, block the URL at the web proxy/firewall]

## MITRE ATT&CK Mapping
**T1566 — Phishing** [add sub-technique if applicable, e.g., T1566.002 — Spearphishing Link]
