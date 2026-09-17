# 📧 Email Alert System — JPMLSolutions Portfolio

A Microsoft Power Platform solution designed to monitor mailbox activity, capture incoming email events, classify them, and store structured alert data in Dataverse for operational monitoring and automation.

This project complements the Task Manager portfolio by showing how Power Platform can handle event-driven processing, Microsoft Graph integration, and rule-based business logic.

---

## 🎯 Project Purpose

The Email Alert System (EAS) is built for environments where email is not just communication, but a source of operational signals.

It supports scenarios such as:

- alerting on incoming operational emails
- parsing email events into structured business data
- monitoring mailbox activity continuously
- creating auditable logs for each processing step
- routing alerts to downstream workflows or business teams

This is a strong example of a low-code, enterprise-ready solution using Dataverse, Power Automate, Graph, and Azure identity/security patterns.

---

## 🏗️ Architecture Overview

```text
┌──────────────────────────────────────────────────────────────┐
│                Microsoft 365 / Exchange / Graph              │
│  Monitored Mailboxes │ Webhooks │ Email Notifications         │
└──────────────────────────────┬───────────────────────────────┘
                               │
                   ┌───────────▼────────────┐
                   │     Power Automate      │
                   │ • SubscriptionCreate    │
                   │ • EmailIngestion        │
                   │ • GetGraphAccessToken   │
                   │ • RuleBasedParse        │
                   │ • SubscriptionRenew     │
                   │ • SubscriptionDelete    │
                   └───────────┬────────────┘
                               │
                   ┌───────────▼────────────┐
                   │      Microsoft Dataverse │
                   │ crb7a_tbl_MonitoredMailbox│
                   │ crb7a_tbl_AlertRule      │
                   │ crb7a_tbl_EmailRecord     │
                   │ crb7a_tbl_ExtractedData   │
                   │ crb7a_tbl_ProcessingLog   │
                   │ crb7a_dic_AlertChannel    │
                   │ crb7a_dic_EmailCategory   │
                   └───────────┬────────────┘
                               │
                   ┌───────────▼────────────┐
                   │        Azure Layer      │
                   │ • App Registration      │
                   │ • Key Vault             │
                   │ • Secret Management     │
                   └────────────────────────┘
```

---

## ⚙️ Solution Information

This repository reflects the Dataverse solution:

- Unique Name: `PortfolioEmailAlertSystem`
- Friendly Name: `Portfolio - EAS - Email Alert System`
- Publisher Prefix: `crb7a_`
- Version: `1.0.0.1`
- Managed: `No`

The solution is built around a processing model where email events are received, validated, parsed, and recorded for traceability and downstream automation.

---

## 🗄️ Dataverse Model

### Main entities

| Table | Purpose |
|---|---|
| `crb7a_tbl_MonitoredMailbox` | Tracks the mailboxes being monitored |
| `crb7a_tbl_AlertRule` | Business logic for alert triggers and conditions |
| `crb7a_tbl_EmailRecord` | Stores the original email payload and metadata |
| `crb7a_tbl_ExtractedData` | Structured values extracted from messages |
| `crb7a_tbl_ProcessingLog` | Execution history, diagnostics, and audit trail |

### Reference dictionaries

| Table | Purpose |
|---|---|
| `crb7a_dic_AlertChannel` | Defines alert delivery mechanisms |
| `crb7a_dic_EmailCategory` | Defines email categories for classification |

---

## ⚡ Power Automate Flows

The solution includes the following cloud flows:

| Flow | Purpose |
|---|---|
| `Flow_GetGraphAccessToken` | Authenticates with Microsoft Graph and refreshes tokens |
| `Flow_SubscriptionCreate` | Creates webhook subscription for monitored mailboxes |
| `Flow_SubscriptionRenew` | Extends webhook validity before expiry |
| `Flow_SubscriptionDelete` | Removes stale subscriptions |
| `Flow_EmailIngestion` | Receives incoming webhook events |
| `Flow_RuleBasedParse` | Parses message content and classifies alert conditions |

These flows are designed with operational resilience in mind:

- secure authentication through Azure and Key Vault
- validation before processing
- event-driven processing model
- audit logging in Dataverse
- clean separation between ingestion, parsing, and alerting logic

---

## ☁️ Azure and Security Considerations

This solution uses:

- Azure App Registration for identity
- Microsoft Graph for mailbox access and subscription management
- Azure Key Vault for secure secret storage
- Dataverse as the system of record for processed alerts

The design follows a secure-by-default pattern, keeping sensitive credentials out of logic definitions and using connection references to manage runtime auth.

---

## 🧠 Why this matters for a portfolio

This project demonstrates multiple strong Power Platform capabilities:

- event-driven automation with Power Automate
- integration with Microsoft Graph and Exchange Online
- secure app identity and secret handling in Azure
- structured data modeling in Dataverse
- enterprise pattern design for operational alerting

It is a good example of a real business use case that goes beyond simple CRUD and shows practical low-code architecture thinking.

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
│   ├── README.md
│   └── solution-assets/
├── Screenshots/
│   └── .gitkeep
└── .git/
```

---

## 🚀 Recommended Next Enhancements

1. Add sample exported records and example payloads.
2. Document the Microsoft Graph permissions required for the mailbox subscriptions.
3. Add a test matrix for webhook validation and parsing edge cases.
4. Extend the architecture with alert routing and notification actions.
5. Connect the solution to a downstream operational dashboard or Teams notifications.

---

## 📌 Notes

This repository is intentionally structured in the same portfolio-ready style as the Task Manager project, but focused on the Email Alert System scenario.

The goal is to show that the same Power Platform stack can support both task management and event-driven operational intelligence.

---

## 👤 Author

JPMLSolutions / LealDeveloper
