# Dataverse Schema for EAS

## Solution
- Unique Name: `PortfolioEmailAlertSystem`
- Version: `1.0.0.1`
- Publisher Prefix: `crb7a`

## Main Entities

### `crb7a_tbl_MonitoredMailbox`
Represents a mailbox that should be monitored for incoming email activity.

Suggested fields:
- Mailbox Name
- Email Address
- Connection Status
- Last Sync
- Is Active

### `crb7a_tbl_AlertRule`
Defines conditions for when an email should trigger an alert.

Suggested fields:
- Rule Name
- Rule Type
- Alert Channel
- Conditions
- Priority
- Is Active

### `crb7a_tbl_EmailRecord`
Stores email payloads captured from Microsoft Graph or webhook events.

Suggested fields:
- Subject
- Sender
- Recipient
- Received Date
- Body
- Message ID
- Raw JSON

### `crb7a_tbl_ExtractedData`
Stores normalized or parsed values extracted from email messages.

Suggested fields:
- Extracted Key
- Extracted Value
- Source Record
- Confidence Score
- Category

### `crb7a_tbl_ProcessingLog`
Stores execution, exception, and auditing data for each flow run.

Suggested fields:
- Run ID
- Flow Name
- Step Name
- Status
- Error Message
- Timestamp

## Lookup / Dictionary Tables

### `crb7a_dic_AlertChannel`
Used to classify the delivery channel for an alert.

### `crb7a_dic_EmailCategory`
Used to classify inbound email type or alert category.

## Relationship Notes
- Each `EmailRecord` can link to one or many `ExtractedData` entries.
- Each `AlertRule` can be associated with monitored mailboxes and categories.
- `ProcessingLog` should be append-only and used for operational traceability.
