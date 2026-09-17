# Power Automate Overview for EAS

## Flow Landscape
The Email Alert System relies on a set of cloud flows to manage the full lifecycle:

1. `Flow_GetGraphAccessToken`
   - Authenticates to Microsoft Graph using app identity or secure credentials.

2. `Flow_SubscriptionCreate`
   - Creates a webhook subscription for monitored mailboxes.

3. `Flow_SubscriptionRenew`
   - Extends subscription lifetime before expiry.

4. `Flow_SubscriptionDelete`
   - Cleans up subscriptions when the configuration is removed.

5. `Flow_EmailIngestion`
   - Receives webhook payloads and validates the message event.

6. `Flow_RuleBasedParse`
   - Applies parsing rules and stores extracted values in Dataverse.

## Design Principles
- Secure token handling via Key Vault
- Try / Catch patterns around core actions
- Logging every step to `crb7a_tbl_ProcessingLog`
- Rule-driven parsing instead of hardcoded assumptions
- Traceable monitoring and operational recovery

## Operational Recommendations
- Monitor webhook expiration dates.
- Track failed subscription renewals.
- Validate message parsing against real email samples.
- Keep the logic modular and easily testable.
