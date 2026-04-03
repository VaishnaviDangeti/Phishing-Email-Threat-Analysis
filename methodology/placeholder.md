# Methodology

## Overview
This document explains exactly how I analyzed each phishing 
email sample — step by step.

---

## Tools Used

| Tool | Purpose |
|------|---------|
| PhishTank | Source of real phishing email samples |
| VirusTotal | URL and domain reputation scanning |
| MXToolbox | Email header analysis |
| Manual analysis | SPF, DKIM, DMARC validation |

---

## Step by Step Process

### Step 1 — Sample Collection
- Visited PhishTank and filtered for active phishing emails
- Focused on samples targeting financial institutions
- Collected 50+ unique samples across different attack types

### Step 2 — Email Header Forensics
For every single email I checked:

**SPF (Sender Policy Framework)**
- Verified if the sending server was authorized
- Most phishing emails FAILED SPF checks

**DKIM (DomainKeys Identified Mail)**
- Checked if email signature was valid
- Spoofed emails had missing or invalid DKIM signatures

**DMARC**
- Checked domain policy for handling failed emails
- Found most targeted domains had weak or no DMARC policy

### Step 3 — URL Analysis
- Extracted all URLs from email body
- Submitted each URL to VirusTotal
- Documented reputation scores and detection flags
- Traced redirect chains to find final landing pages

### Step 4 — IOC Extraction
- Documented all malicious domains found
- Recorded spoofed sender IPs
- Catalogued obfuscated redirect URLs
- Assigned sample IDs (PH-001 to PH-050+)

### Step 5 — Campaign Clustering
- Grouped similar emails by attack pattern
- Identified 3 distinct campaign types
- Mapped IOCs to each campaign

### Step 6 — Report Writing
- Wrote individual threat report for each campaign
- Documented attack vectors, IOCs, and defensive controls
- Calculated classification accuracy

---

## Results
- 50+ samples analyzed
- 32+ IOCs extracted
- 3 campaigns identified
- 90%+ classification accuracy achieved
