# Azure Setup for EAS

## Overview
The Email Alert System relies on Azure resources and Microsoft 365 connectivity to authenticate and process mailbox events.

## Core Components
- Azure App Registration
- Microsoft Graph permissions
- Azure Key Vault
- Dataverse connection references
- Office 365 connector usage

## Recommended Configuration
1. Register an application in Microsoft Entra ID.
2. Grant Graph permissions such as:
   - Mail.Read
   - Mail.ReadWrite
   - Mail.Send
   - User.Read
   - offline_access
3. Store confidential values in Azure Key Vault.
4. Map secure values to Power Automate connection references.
5. Validate token refresh logic in the Graph access flow.

## Security Best Practices
- Do not hardcode secrets in flows.
- Use managed connections and Key Vault references.
- Rotate credentials regularly.
- Restrict app permissions to the minimum required.

## Typical Secrets
- Tenant ID
- Client ID
- Client Secret
- Subscription ID
- Resource URIs / application URLs
