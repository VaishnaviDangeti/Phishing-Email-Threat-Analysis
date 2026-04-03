# Phishing Email Threat Analysis

## What is this project?
I analyzed 50+ real phishing emails from PhishTank to understand 
how attackers target financial institutions. This was a hands-on 
project where I did everything manually from checking email 
headers to scanning URLs on VirusTotal.

---

## Why I did this
I kept reading about phishing being the #1 attack vector in fintech 
and banking. I wanted to actually see what these emails look like, 
how they're built, and how analysts detect them not just read 
about it theoretically.

---

## What I did

**Step 1 — Collected samples**
Pulled 50+ active phishing email samples from PhishTank, focusing 
on ones targeting banks and financial platforms.

**Step 2 — Analyzed email headers**
For each email I manually checked:
- SPF records (is the sender server authorized?)
- DKIM signatures (was the email tampered with?)
- DMARC policy (does the domain even have protection?)

Most spoofed emails completely failed all three checks.

**Step 3 — Checked every URL**
Ran all suspicious links through VirusTotal. Found a lot of 
obfuscated redirect chains URLs that look harmless but 
redirect 3-4 times before landing on a fake login page.

**Step 4 — Documented everything**
Extracted 30+ IOCs and noticed patterns the same malicious 
domains kept appearing across different emails.

---

## What I found

I spotted 3 clear campaign patterns:

**Campaign 1 — Fake Bank Login Pages**
Emails pretending to be from banks asking users to 
"verify their account." Classic credential harvesting.

**Campaign 2 — Fake Invoice Emails**
Targeted at people in finance roles. Spoofed vendor 
email addresses with malicious PDF attachments.

**Campaign 3 — Account Takeover Attempts**
Disguised as fintech app security alerts with 
links that steal session tokens.

---

## Results
- Classified 90%+ of emails correctly as malicious
- Found 30+ IOCs across all samples
- Wrote individual threat reports for all 3 campaigns

---

## Tools I used
- PhishTank — phishing email samples
- VirusTotal — URL and domain scanning
- MXToolbox — header analysis
- Manual analysis for SPF/DKIM/DMARC checks

---

## What I learned
Honestly the biggest thing I learned is how easy it is to 
spoof an email when a domain has no DMARC policy. Most 
small fintech companies don't have this configured properly 
 which is a huge risk.

---

## About me
I'm Vaishnavi Dangeti, a cybersecurity student interested 
in threat intelligence and blue team security. This project 
was fully self-initiated . I wanted real hands-on experience 
beyond just certifications.

GitHub: github.com/VaishnaviDangeti
