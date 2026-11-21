# Small Business Security & Compliance Assessment (Salon & Retail Operations)

## 1. Executive Summary
This assessment evaluates the cybersecurity, data privacy, and payment-handling posture of a local independent hair and beauty salon (anonymized as **"Irving Beauty & Barber Studio"**). The business processes in-person credit/debit card payments via a cloud-based Point-of-Sale (POS) tablet, manages client contact and appointment records online, and provides guest Wi-Fi on site.

* **Assessment Objective:** Identify operational security gaps, map existing practices to **CIS Critical Security Controls v8 (Implementation Group 1)** and **PCI DSS v4.0**, and establish a prioritized Risk Register with low-cost remediation steps suitable for a small business budget.
* **Key Outcome:** Reduced payment-card exposure and unauthorized network access risks by separating guest Wi-Fi, enforcing multi-factor authentication (MFA) on POS/booking accounts, and formalizing customer data retention rules.

---

## 2. Scope & Critical Assets
| Asset Category | Specific Assets | Data Handled | Applicable Standards |
| :--- | :--- | :--- | :--- |
| **Payment Systems** | Cloud POS terminal & card reader | Cardholder data (encrypted at swipe), transaction receipts | PCI DSS v4.0 (SAQ B-IP / P2PE) |
| **Client Booking & CRM** | Cloud scheduling & client profile software | Client names, phone numbers, email addresses, service notes | CIS Controls v8 (Data Protection) |
| **Network Infrastructure** | ISP wireless router & guest Wi-Fi network | POS payment traffic, business admin traffic, visitor traffic | PCI DSS Req. 1 & 2; CIS Control 12 |
| **Administrative Devices** | Owner smartphone & back-office tablet | Business email, Google Business Profile, payroll/vendor portals | CIS Controls v8 (Access Control) |

---

## 3. Control Gap Analysis (CIS Controls v8 & PCI DSS)

| Control ID | Framework Reference | Control Requirement | Current State | Gap Status |
| :--- | :--- | :--- | :--- | :--- |
| **CIS 1.1 / 2.1** | CIS v8 (IG1) | Maintain an accurate inventory of authorized devices and software | No formal asset list; personal and business devices mixed | **Gap Identified** |
| **CIS 3.3 / 3.4** | CIS v8 (IG1) | Configure data access control lists and enforce data retention limits | Staff share a single front-desk login for appointment scheduling | **Gap Identified** |
| **CIS 6.3 / 6.5** | CIS v8 (IG1) | Require MFA for externally exposed applications and administrative accounts | Password-only login enabled on POS admin portal and business email | **High-Priority Gap** |
| **PCI 1.3 / 2.2** | PCI DSS v4.0 | Isolate cardholder data environment (CDE) from untrusted guest networks | POS tablet and guest customers connect to the same Wi-Fi SSID | **High-Priority Gap** |
| **PCI 9.5 / CIS 4.1** | PCI DSS / CIS v8 | Physically secure POS card readers against tampering and enforce auto-lock | Card reader kept at staffed front desk; tablet auto-lock set to 15 mins | **Partial** |

---

## 4. Prioritized Risk Register

| Risk ID | Risk Description | Likelihood | Impact | Overall Risk | Recommended Remediation | Target Timeline |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **RSK-01** | **Shared Wi-Fi Network:** Guest devices share the same wireless network as the POS terminal, exposing payment traffic to potential sniffing or lateral attacks. | High | High | **Critical** | Enable the router's isolated **Guest Wi-Fi network** for clients and restrict the primary encrypted WPA3 SSID strictly to the POS tablet. | Immediate (Week 1) |
| **RSK-02** | **No MFA on Admin & POS Portals:** Credential stuffing or phishing could allow an attacker to hijack business email, payout bank routing, or client PII. | High | High | **Critical** | Enable app-based or SMS **Multi-Factor Authentication (MFA)** across the POS platform, booking software, and business Google account. | Immediate (Week 1) |
| **RSK-03** | **Shared Front-Desk Credentials:** Multiple stylists use one shared login for the booking system, preventing audit accountability if client records are exported or altered. | Medium | Medium | **Moderate** | Create individual staff role-based accounts with least-privilege access (view schedule only; restrict data export and financial settings to owner). | Short-Term (Weeks 2–3) |
| **RSK-04** | **Unsecured Endpoint Session Timeout:** Front-desk tablet remains unlocked for 15 minutes when unattended, exposing client phone numbers and addresses. | Medium | Medium | **Moderate** | Configure automatic screen lock to **2 minutes** of inactivity and require a strong 6-digit PIN or biometric unlock. | Immediate (Week 1) |
| **RSK-05** | **Lack of Incident Response & Device Loss Plan:** No documented steps if the business phone or POS tablet is lost or stolen. | Low | High | **Moderate** | Document a 1-page Incident Response checklist (remote wipe steps via Find My Device, bank/POS processor hotline, and password reset procedure). | Short-Term (Month 1) |

---

## 5. Key Takeaways & Remediation Roadmap
* **Zero-Cost Quick Wins (Completed/Week 1):** Isolated guest Wi-Fi, enforced MFA on all administrative accounts, shortened tablet screen-lock timeout to 2 minutes, and changed default ISP router admin credentials.
* **Governance Documentation (Weeks 2–4):** Established a 1-page Acceptable Use & Device Security Policy for staff and a monthly checklist to verify POS software updates and inspect card readers for physical tampering.
