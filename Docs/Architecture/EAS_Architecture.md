# EAS Architecture

## Overview
The Email Alert System is designed to watch mailbox activity and transform raw email events into structured, audit-friendly records inside Dataverse.

## Core Flow
1. A monitored mailbox receives a new email.
2. Microsoft Graph subscription or webhook triggers a Power Automate flow.
3. The ingestion flow validates the event and stores the email payload.
4. A parsing flow evaluates alert rules against the message content.
5. Structured extracted data is stored in Dataverse.
6. Operational logs and diagnostics remain available for review.

## Design Principles
- Secure by default
- Event-driven rather than polling-centric
- Rule-based parsing for scale and maintainability
- Auditability through processing logs
- Decoupling of ingestion, parsing, and downstream actions

## Data Flow
- Source: Microsoft 365 mailbox events
- Middleware: Power Automate cloud flows
- System of record: Dataverse
- Security layer: Azure Key Vault + identity configuration

## Operational Concern Areas
- Webhook validation and renewal
- Failed Graph token refresh
- Message content parsing quality
- Duplicate or repeated event handling
- Handling malformed payloads and exceptions

## Suggested Future Enhancements
- notification routing via Teams or email
- classification engine using rules or AI assistance
- dashboard for alert trends and backlog volume
- SLA monitoring around alert response times
