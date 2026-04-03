# Phishing Campaign Threat Reports

## Campaign 1 — Credential Harvesting

**Target:** Retail banking users  
**Samples Analyzed:** PH-001, PH-003, PH-004, PH-007, PH-009, PH-010

### What I found
These emails were pretending to be from banks asking users to 
verify their account or reset their password. The links led to 
fake login pages that looked identical to real banking portals.

### How the attack worked
1. Victim receives email appearing to be from their bank
2. Email claims account will be suspended unless they verify
3. Link redirects through 2-3 domains before landing on fake page
4. Victim enters credentials — attacker captures them instantly

### IOCs Found
- extromtechnology.com
- bank-security-reset.com
- customer-secure-update.com
- secure-bank-update.com
- security-login-check.com
- bank-alert-update.com

### Email Authentication Results
- SPF — FAIL (sender not authorized)
- DKIM — FAIL (signature missing)
- DMARC — FAIL (no policy enforced)

### Defensive Controls
- Enforce DMARC p=reject on all banking domains
- Block newly registered domains at email gateway
- Train users to verify URLs before entering credentials

---

## Campaign 2 — Invoice Fraud

**Target:** Finance departments and accounts teams  
**Samples Analyzed:** PH-002, PH-005, PH-008, PH-011, PH-014, PH-017

### What I found
These emails spoofed vendor email addresses and sent fake 
invoices asking for urgent payments. Very convincing because 
they used real company names and logos.

### How the attack worked
1. Attacker spoofs a known vendor's email address
2. Sends urgent invoice with slightly modified payment details
3. Finance team processes payment to attacker's account
4. Fraud discovered only after payment is made

### IOCs Found
- secure-payment-check.com
- invoice-resolution.net
- vendor-billing-check.com
- invoice-payment-review.com
- vendor-payment-check.net
- invoice-processing-alert.com

### Email Authentication Results
- SPF — FAIL (domain spoofed)
- DKIM — FAIL (no signature)
- DMARC — NONE (domain unprotected)

### Defensive Controls
- Verify all invoice payment requests via phone call
- Flag emails with lookalike vendor domains
- Implement strict SPF records for all vendor domains

---

## Campaign 3 — Account Takeover

**Target:** Fintech app users  
**Samples Analyzed:** PH-006, PH-012, PH-015, PH-016, PH-021, PH-024

### What I found
These emails pretended to be security alerts from fintech apps 
warning users about suspicious activity. Links contained session 
hijacking payloads designed to steal authentication tokens.

### How the attack worked
1. Victim receives fake security alert email
2. Clicks link to "secure their account"
3. Redirect chain captures session token in background
4. Attacker gains full account access without needing password

### IOCs Found
- account-review-alert.com
- account-monitoring-alert.com
- access-alert-review.com
- identity-update-center.com
- account-reset-check.com
- secure-login-monitor.com

### Email Authentication Results
- SPF — FAIL
- DKIM — FAIL
- DMARC — FAIL

### Defensive Controls
- Implement MFA on all fintech accounts
- Use short-lived session tokens with strict expiry
- Deploy real-time anomaly detection for login attempts

---

## Overall Summary

| Campaign | Emails Analyzed | IOCs Found | Authentication Failures |
|----------|----------------|------------|---------------|
| Credential Harvesting | 18 | 12 | SPF, DKIM, DMARC |
| Invoice Fraud | 17 | 11 | SPF, DKIM, DMARC |
| Account Takeover | 15 | 9 | SPF, DKIM, DMARC |
| **Total** | **50** | **32+** | — |
