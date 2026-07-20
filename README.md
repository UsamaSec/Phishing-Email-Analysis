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

![VirusTotal flagging the email's originating IP as malicious, tied to a known Tor exit node](screenshots/virustotal-ip-result.png)

## What I Learned
Learned to trace a spoofing attempt through the full header chain — the visible "From" address looked legitimate, but the Return-Path and Reply-To headers revealed a misspelled lookalike domain, which wouldn't be visible without inspecting raw headers directly. Also learned that SPF/DKIM/DMARC failures alone can reliably flag a spoofed sender even before checking content. The most unexpected finding was that the fictional IP address I selected for the sample's Received header turned out to be a real, currently-flagged malicious IP tied to a known Tor exit node — a reminder that infrastructure-level indicators (like IPs) often carry real-world reputation data even in constructed examples, and that attackers commonly use anonymizing infrastructure like Tor to mask their origin.

## Next Steps
Analyze a second, real-world phishing sample from a spam folder for comparison. Consider extending the Python log analyzer from my SOC-Log-Analyzer project to automate basic header/IOC extraction from .eml files.
