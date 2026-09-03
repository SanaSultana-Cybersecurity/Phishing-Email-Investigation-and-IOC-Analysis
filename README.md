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
