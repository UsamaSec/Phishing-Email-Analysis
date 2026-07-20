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

![MXToolbox authentication results](screenshots/mxtoolbox-results.png)

## IOC Extraction

| Indicator | Type | VirusTotal Result |
|-----------|------|--------------------|
| [URL/domain] | URL | [Clean / Flagged - X/90 vendors] |
| [Sender IP] | IP | [result] |
| [Attachment hash, if any] | File hash | [result] |

![VirusTotal lookup results](screenshots/virustotal-results.png)

## Verdict
[State clearly: Malicious / Phishing confirmed / Suspicious / Benign - and why, referencing the specific evidence above]

## Recommendation
[What should happen next in a real environment - e.g., block sender domain, report to email provider, user awareness reminder, block the URL at the web proxy/firewall]

## MITRE ATT&CK Mapping
**T1566 — Phishing** [add sub-technique if applicable, e.g., T1566.002 — Spearphishing Link]
