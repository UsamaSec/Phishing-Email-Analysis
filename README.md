# Phishing Email Analysis

Analysis of a phishing email sample — header inspection, sender authentication checks (SPF/DKIM/DMARC), IOC extraction, and spoofing detection, documented as a formal analyst report. Demonstrates the email triage and investigation process a SOC analyst performs when a user reports a suspicious message.

## Why This Project

Phishing analysis is one of the most common day-to-day tasks for an entry-level SOC analyst. This project applies the same investigative approach used in my SOC Analyst role at Dar Al Waffa Digital Media to a self-built, safe sample — demonstrating header analysis, IOC extraction, and structured reporting without needing to handle live malicious content.

## Tools Used
Email header analysis · MXToolbox (SPF/DKIM/DMARC verification) · VirusTotal (safe URL/IOC lookup)

## What This Project Demonstrates
1. Identifying signs of spoofing and social engineering in email content
2. Analyzing raw email headers to trace true origin vs. claimed sender
3. Verifying SPF, DKIM, and DMARC authentication results
4. Safely extracting and investigating IOCs (URLs, domains, sender IPs) without direct interaction
5. Documenting findings in a structured analyst report with a clear verdict and recommendation

## Sample Used
A self-constructed phishing email sample, built to safely demonstrate realistic phishing characteristics (spoofed sender, urgency language, suspicious link) without involving any live malicious content. [If a second real, already-neutralized sample from a spam folder is added later, describe it here.]

## Full Report
See [analysis-report.md](analysis-report.md) for the full header analysis, IOC findings, and verdict.

## Sample Screenshot

![Header analysis results](screenshots/header-analysis.png)

## What I Learned
[Fill in once completed]

## Next Steps
[Optional — e.g., analyze a second real-world sample, or build a small Python script to automate header/IOC extraction]
