# Phishing-Email-Investigation-and-IOC-Analysis
SOC L1 phishing email investigation and IOC analysis

## Email Header Analysis

### Sender Information

| Field | Value |
| From | `adminKCwSu@schubert-cz.riddler.com` |
| Return-Path | `adminKCwSu@schubert-cz.riddler.com` |
| Recipient | `jose@monkey.org` |
| Subject | `Warning: [Secure your account] Update your mailbox 2025` |
| Source IP | `147.124.214.239` |

### Email Authentication

| Authentication | Result |
| SPF | None |
| DKIM | Invalid DKIM record |
| DMARC | None |

### Received Header

The email was received from:

`147.124.214.239`

The connection was established to the mail server `kerk.email`.

> The source IP was investigated using VirusTotal and multiple security vendors flagged it as suspicious/malicious.

> ## Email Body Analysis

The email uses an account-verification theme to create urgency and convince the recipient to click a verification link.

### Suspicious Message

> "will stop sending and receiving emails if not verified."

The email also states:

> "To maintain your account with us, please check below"

### Verification Link

The email contains a **VERIFY** button directing the recipient to an external domain:

`hxxps://mewww[.]standard[.]us-east-1[.]oortstorage[.]com/uehe`

The recipient's email address is also embedded in the URL fragment:

`#jose@monkey[.]org`

### Phishing Indicators

- Urgent account-verification request
- Threat of email service disruption
- Credential/account verification lure
- External verification domain
- Suspicious source IP
- Malicious URL reputation
- Malicious destination-domain reputation

- ## URL Investigation

The VERIFY button in the email redirects the user to an external URL.

### Extracted URL

`hxxps://mewww[.]standard[.]us-east-1[.]oortstorage[.]com/uehe`

### VirusTotal Result

The URL was submitted to VirusTotal for reputation analysis.

**Result:** Multiple security vendors detected the URL as malicious.

This supports the conclusion that the link is associated with phishing activity.


##  Domain Investigation

### Destination Domain

`mewww[.]standard[.]us-east-1[.]oortstorage[.]com`

The domain was extracted from the `href` value of the VERIFY button in the email HTML.

### VirusTotal Result

**Result:** Multiple security vendors detected the destination domain as malicious.

The domain is therefore considered a malicious IOC in this investigation.


##  Source IP Investigation

### Source IP

`147.124.214.239`

The IP address was identified from the email's `Received` header.

### VirusTotal Result

The IP address was investigated using VirusTotal.

**Result:** Multiple security vendors flagged the IP address as suspicious/malicious.

This increases confidence that the email originated from suspicious infrastructure.


##  Indicators of Compromise (IOCs)

| IOC Type | Indicator | Reputation |
|---|---|---|
| IP Address | `147.124.214.239` | Malicious/Suspicious |
| Domain | `mewww[.]standard[.]us-east-1[.]oortstorage[.]com` | Malicious |
| URL | `hxxps://mewww[.]standard[.]us-east-1[.]oortstorage[.]com/uehe` | Malicious |
| Sender Domain | `schubert-cz[.]riddler[.]com` | No malicious reputation observed during investigation |

> The URL and domain have been defanged to prevent accidental access.
>
> ## Phishing Indicators

The following indicators were identified during the investigation:

- Urgent account verification request
- Threat that email services would stop if verification was not completed
- Suspicious sender infrastructure
- SPF authentication result: None
- DKIM authentication result: Invalid DKIM record
- DMARC authentication result: None
- Malicious source IP reputation
- Malicious destination domain reputation
- Malicious URL reputation
- External verification page used to potentially harvest credentials


## MITRE ATT&CK Mapping

| Tactic | Technique | Relevance |
|---|---|---|
| Initial Access | T1566 - Phishing | The attacker used a phishing email to target the recipient. |
| Credential Access | T1056.002 - Input Capture: GUI Input Capture | The verification link may lead to a fake login page designed to capture credentials. |

---

## SOC L1 Response

### Immediate Actions

1. Quarantine the phishing email.
2. Block the malicious URL and domain using available security controls.
3. Investigate whether other users received the same email.
4. Search email and proxy logs for clicks to the malicious URL.
5. Check authentication logs for suspicious login activity.
6. If credentials were submitted, reset the affected user's password.
7. Review the affected account for unauthorized activity.
8. Escalate to the appropriate security team if account compromise is suspected.


##  Final Verdict

### CONFIRMED PHISHING - CREDENTIAL PHISHING

The email was determined to be a phishing attempt based on multiple correlated indicators, including:

- Suspicious email authentication results
- Malicious source IP reputation
- Malicious destination domain
- Malicious URL
- Urgent account-verification messaging
- Attempt to direct the recipient to an external verification page

The primary objective appears to be **credential theft through a fake account verification process**.



##  Key Learnings

- Email headers can reveal important infrastructure and authentication information.
- SPF, DKIM, and DMARC results should be analyzed together with other evidence.
- URLs and domains should be investigated before being accessed.
- VirusTotal can help identify malicious infrastructure and reputation.
- Multiple correlated indicators provide stronger evidence than a single detection.
- A SOC L1 analyst should document findings, extract IOCs, determine the verdict, and recommend appropriate containment actions.
