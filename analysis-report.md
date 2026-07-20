# Phishing Email Analysis Report

## Summary
[2-3 sentences: what the email claimed to be, what it was actually trying to do, and your overall verdict]

## Email Overview
| Field | Value |
|-------|-------|
| Claimed sender | [e.g., "IT Support <it-support@company.com>"] |
| Subject line | [subject] |
| Date received | [date] |
| Delivered to | [recipient, or "test inbox" if self-constructed] |

## Red Flags Identified (Content-Level)
- [ ] Urgency/pressure language (e.g., "act now," "account will be suspended")
- [ ] Generic greeting instead of personalized name
- [ ] Suspicious/mismatched sender domain
- [ ] Embedded link with display text differing from actual URL
- [ ] Unexpected attachment
- [ ] Poor grammar/spelling inconsistent with claimed sender
- [ ] Request for credentials, payment, or sensitive info

[List which of these applied, with 1 sentence each explaining what you saw]

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
