# 📧 Email Alert System (EAS)

<div align="center">

![GitHub repo](https://img.shields.io/badge/Power%20Platform-Dataverse%20%2B%20Power%20Automate-0078D4?style=for-the-badge)
![GitHub repo](https://img.shields.io/badge/Project-Email%20Alert%20System-6A5ACD?style=for-the-badge)
![GitHub repo](https://img.shields.io/badge/Status-Portfolio%20Ready-2ECC71?style=for-the-badge)

</div>

A Microsoft Power Platform solution designed to monitor mailbox activity, ingest email events, classify them, and store structured alert data in Dataverse for operational automation and traceability.

This project complements the Task Manager portfolio by demonstrating a more event-driven and integration-heavy scenario using Microsoft Graph, Power Automate, Dataverse, and Azure security services.

---

## 🎯 Business Value

The EAS is built for operational scenarios where email is a business signal rather than just communication.

Examples include:

- alerting on incoming operational emails
- parsing customer or support emails into structured records
- monitoring mailbox activity continuously
- logging each processing event for auditability
- routing business alerts into downstream automation

---

## 🏗️ Architecture Overview

```text
┌──────────────────────────────────────────────────────────────┐
│             Microsoft 365 / Exchange / Microsoft Graph      │
│  Monitored Mailboxes │ Webhooks │ Email Events               │
└───────────────────────────────┬──────────────────────────────┘
                                │
                    ┌───────────▼────────────┐
                    │    Power Automate       │
                    │ • GetGraphAccessToken   │
                    │ • SubscriptionCreate    │
                    │ • SubscriptionRenew     │
                    │ • SubscriptionDelete    │
                    │ • EmailIngestion        │
                    │ • RuleBasedParse        │
                    └───────────┬────────────┘
                                │
                    ┌───────────▼────────────┐
                    │    Microsoft Dataverse  │
                    │ crb7a_tbl_MonitoredMailbox │
                    │ crb7a_tbl_AlertRule        │
                    │ crb7a_tbl_EmailRecord      │
                    │ crb7a_tbl_ExtractedData    │
                    │ crb7a_tbl_ProcessingLog    │
                    │ crb7a_dic_AlertChannel     │
                    │ crb7a_dic_EmailCategory    │
                    └───────────┬────────────┘
                                │
                    ┌───────────▼────────────┐
                    │      Azure Layer        │
                    │ • App Registration      │
                    │ • Key Vault             │
                    │ • Secret Management     │
                    └────────────────────────┘
```

---

## ⚙️ Solution Information

The repository reflects the following Dataverse solution:

- Unique Name: `PortfolioEmailAlertSystem`
- Friendly Name: `Portfolio - EAS - Email Alert System`
- Publisher Prefix: `crb7a_`
- Version: `1.0.0.1`
- Managed: `No`

The design is centered on a processing lifecycle where email events are received, validated, parsed, classified, and logged for operational traceability.

---

## 📊 Core Components

### Dataverse model

| Entity | Purpose |
|---|---|
| `crb7a_tbl_MonitoredMailbox` | Tracks the mailboxes monitored by the solution |
| `crb7a_tbl_AlertRule` | Stores business rules used to detect email-based alerts |
| `crb7a_tbl_EmailRecord` | Stores raw email data and metadata |
| `crb7a_tbl_ExtractedData` | Holds structured values extracted from the email content |
| `crb7a_tbl_ProcessingLog` | Auditable log of operations, errors, and process steps |

| Dictionary | Purpose |
|---|---|
| `crb7a_dic_AlertChannel` | Defines how alerts are propagated |
| `crb7a_dic_EmailCategory` | Classifies incoming messages by type or scenario |

### Power Automate flows

| Flow | Purpose |
|---|---|
| `Flow_GetGraphAccessToken` | Authenticates to Microsoft Graph using secure credentials |
| `Flow_SubscriptionCreate` | Creates webhook subscriptions for mailbox monitoring |
| `Flow_SubscriptionRenew` | Refreshes subscriptions before expiry |
| `Flow_SubscriptionDelete` | Removes stale or disabled subscriptions |
| `Flow_EmailIngestion` | Receives mailbox events and validates payloads |
| `Flow_RuleBasedParse` | Applies alert rules and stores normalized output |

---

## 🔐 Azure and Security Model

This solution makes use of:

- Azure App Registration for external identity and Graph access
- Azure Key Vault to protect connection secrets and credentials
- Dataverse connection references for secure, reusable runtime access
- Microsoft Graph permissions aligned with mailbox monitoring needs

The implementation follows a secure-by-default posture, keeping sensitive values outside the workflow logic itself.

---

## 🧠 Why this is a strong portfolio project

This repository demonstrates a realistic low-code enterprise scenario that combines:

- event-driven automation
- external system integration
- secure identity configuration
- structured data modeling
- operational monitoring and auditability

It shows that Power Platform is not limited to form-based apps or simple task workflows; it can support intelligent business monitoring and alert-driven processes.

---

## 📁 Repository Structure

```text
JPMLSolutions-EAS-EmailAlertSystem/
├── README.md
├── .gitignore
├── Docs/
│   ├── Architecture/
│   │   └── EAS_Architecture.md
│   ├── Azure/
│   │   └── Azure_Setup.md
│   ├── Dataverse/
│   │   └── Dataverse_Schema.md
│   └── PowerAutomate/
│       └── PowerAutomate_Overview.md
├── Solution/
│   ├── EAS_Entities.zip
│   └── README.md
├── Screenshots/
│   └── .gitkeep
└── .git/
```

---

## 🚀 Recommended Next Steps

1. Add real sample email payloads and parsed outputs.
2. Document Microsoft Graph permissions and consent requirements.
3. Add a test matrix for webhook validation and parsing edge cases.
4. Extend the architecture with Teams or email notification actions.
5. Add dashboards or reporting views for alert volume and SLA tracking.

---

## 📌 Notes

This repository is intentionally structured to align with the style of a portfolio project and to illustrate a practical enterprise Power Platform solution.

It complements the Task Manager project and highlights a second use case: operational intelligence through email-triggered automation.

---

## 👤 Author

JPMLSolutions / LealDeveloper
