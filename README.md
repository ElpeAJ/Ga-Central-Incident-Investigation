# ⚠️ In progress - Due Date: September 30th, 2026

# Ga Central Municipal District: Incident Investigation
### Enterprise Cyber Forensics & Financial Fraud Analysis Case Study
**Investigator:** Elpedia J. Arthur (Elpe)  
**Program Track:** Tech4Dev Cybersecurity Sprint — Capstone Project  
**Target Environment:** Public Sector Local Government Network Architecture (Simulated)

---

## 📋 Executive Summary
On August 25, 2026, an adversary successfully intercepted and weaponized the active session tokens of the Municipal Finance Officer (MFO), Mrs. Yaa Afriyie, at the Ga Central Municipal District. By bypassing established multi-factor authentication (MFA) via a sophisticated **Session Hijacking** vector, the threat actor gained unauthorized administrative control over the primary municipal email ecosystem (`ExchangeMail`). 

The compromised session was subsequently leveraged to intercept internal procurement communications, manipulate valid digital invoices, and inject fraudulent banking coordinates. This unauthorized intervention successfully diverted a critical public infrastructure milestone payment of **GHS 450,000**, originally earmarked for the *Ablekuma-Anyaa Road Rehabilitation Project*, into an unverified external banking container.

This repository serves as a comprehensive forensic repository containing multi-source logs, connection matrices, and programmatic runbooks deployed to isolate the root vulnerability, map lateral movement, and establish robust transaction-verification frameworks.

---

## Repository Architecture & Data Footprint
To facilitate scalable anomaly detection and programmatic correlation via Python and automated AI analytic pipelines, all forensic artifacts have been standardized into structured schemas:

```text
├── evidence/
│   ├── network_logs.csv       # Edge routing traffic capturing byte volumes and protocol shifts
│   ├── system_logs.csv        # Multi-component logs capturing authentication and mail-rule injection events
│   └── firewall_traffic.csv   # Perimeter state changes logging access states and egress rule failures
├── analysis/
│   └── wireshark_notes.md     # Granular packet filtering logic and cleartext credential sniffing analysis
└── README.md                  # Executive Brief and project master documentation
```

---

## Incident Attack Timeline (Forensic Correlation Matrix)

By correlating temporal anomalies across perimeter networks, operating systems, and host applications, the incident lifecycle was reconstructed into the following high-fidelity timeline:

| Timestamp (UTC) | Source Entity | Event Category | Forensic Observation & System Impact |
| :--- | :--- | :--- | :--- |
| **08:08:14Z** | `192.168.10.45` | Authentication | MFO establishes legitimate connection; webmail assigns session `token_id=GAC-993821-X3`. |
| **11:30:15Z** | `192.168.10.45` | Protocol Vulnerability | Network gateway permits plain-text **HTTP (Port 80)** transmission over WAN. Session cookie exposed to network sniffing. |
| **14:22:05Z** | `45.138.99.12` | Token Hijack | External adversarial node injects stolen token string `GAC-993821-X3`. Bypasses active MFA checks. |
| **14:26:11Z** | `45.138.99.12` | Unauthorized Persistence | Malicious routing rule injected into exchange core to BCC all `"invoice;payment"` lines to rogue inbox. |

---

## Investigation Methodology & Core Technical Focus
This 8-week progressive sprint evaluates infrastructure deficiencies across several critical technological domains:

1. **Network Topology & Egress Vulnerabilities (Week 2):** Audit of perimeter firewall constraints to identify why unencrypted outbound cleartext payloads were authorized to execute across untrusted domains.
2. **Threat Surface Detection & Header Analysis (Week 3):** Dissection of email server transaction blocks and concurrent connection anomalies tracking geo-location tracking errors.
3. **Incident Containment & Governance Controls (Week 5):** Designing emergency localized policy frameworks to mandate cryptographically isolated administrative endpoints.
4. **AI-Driven Threat Hunting with Human Oversight (Week 7):** Leveraging predictive large-scale telemetry models to systematically pars large-volume CSV datasets while verifying results via expert analyst filtering.

---

## Core Remediation Strategy
*   **Cryptographic Enforcement:** Implement immediate Global HTTP Strict Transport Security (HSTS) rewriting configurations across all municipal ingress/egress corridors.
*   **Contextual Session Expiry:** Deploy risk-based conditional access profiles to instantly invalidate tokens experiencing geographic velocity anomalies (e.g., concurrent access from local subnets and foreign proxies).
*   **Dual-Authorization Transaction Controls:** Establish multi-tiered offline token validations for any outbound financial disbursements exceeding GHS 50,000.


<img width="945" height="313" alt="Screenshot 2026-08-17 at 10 28 17 PM" src="https://github.com/user-attachments/assets/26f534da-c176-4fcb-be51-f8cdda50413b" />

<!-- <p>

├── README.md               <-- The "Face" of your project (Executive Summary & Timeline)
├── evidence/
│   ├── email_headers.txt   <-- Mock malicious headers (with spoofed domains/session tokens)
│   └── network_logs.csv    <-- Mock firewall logs showing the attacker's unusual IP address
├── analysis/
│   ├── wireshark_notes.md  <-- Your step-by-step packet filtering logic (using your LetsDefend skills)
│   └── timeline.json       <-- A JSON array mapping out the attack step-by-step
└── deliverables/
    ├── Incident_Report.pdf <-- The final comprehensive professional text report
    └── Presentation.pdf    <-- The export of your Demo Day slide deck
</p> -->
