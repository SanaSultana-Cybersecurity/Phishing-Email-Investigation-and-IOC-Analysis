# Indicators of Compromise (IOCs)

The following IOCs were extracted during the phishing email investigation.

| Type | IOC | Description |
| IP Address | `147.124.214.239` | Source IP identified in the email headers |
| Domain | `mewww[.]standard[.]us-east-1[.]oortstorage[.]com` | Malicious destination domain |
| URL | `hxxps://mewww[.]standard[.]us-east-1[.]oortstorage[.]com/uehe` | Malicious URL contained in the VERIFY button |
| Sender Domain | `schubert-cz[.]riddler[.]com` | Sender domain observed in the email |

## IOC Investigation

- The source IP was investigated using VirusTotal and was flagged by multiple security vendors.
- The destination domain was flagged as malicious by multiple security vendors.
- The destination URL was flagged as malicious by multiple security vendors.
- The sender domain had no malicious reputation observed during the investigation.

> URLs and domains are defanged to prevent accidental access.
