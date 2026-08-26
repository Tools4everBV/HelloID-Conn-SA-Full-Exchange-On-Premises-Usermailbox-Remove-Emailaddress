# HelloID-Conn-SA-Full-Exchange-On-Premises-Usermailbox-Remove-Emailaddress

| :information_source: Information                                                                                                                                                                                                                                                                                                                                                          |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| This repository contains the connector and configuration code only. The implementer is responsible for acquiring the connection details such as username, password, certificate, etc. You might even need to sign a contract or agreement with the supplier before implementing this connector. Please contact the client's application manager to coordinate the connector requirements. |

## Description

_HelloID-Conn-SA-Full-Exchange-On-Premises-Usermailbox-Remove-Emailaddress_ is a template designed for use with HelloID Service Automation (SA) Delegated Forms. It can be imported into HelloID and customized according to your requirements.

By using this delegated form, you can remove secondary email addresses from Exchange On-Premises user mailboxes. The following options are available:

1.  Search for user mailboxes by name, alias, SAM account name, or primary SMTP address
2.  Select the target mailbox from the search results
3.  View all secondary email addresses (primary email address is excluded from the list)
4.  Select one or multiple email addresses to remove
5.  The selected email addresses are removed from the mailbox
6.  Audit logs are generated for all operations

## Getting started

### Requirements

- **Exchange On-Premises Environment**:<br>
  A working Exchange On-Premises server with PowerShell remoting enabled. The Exchange server must be accessible from the HelloID agent.
- **Service Account**:<br>
  A service account with sufficient permissions to manage mailboxes in Exchange On-Premises. The account should have the "Recipient Management" role or equivalent permissions to modify mailbox email addresses.
- **PowerShell Remoting**:<br>
  PowerShell remoting must be enabled on the Exchange server, and the HelloID agent must be able to establish a remote session using the configured connection URI.
- **Network Connectivity**:<br>
  The HelloID agent must have network access to the Exchange server on the required ports (typically port 80 or 443 for HTTP/HTTPS).

### Connection settings

The following user-defined variables are used by the connector.

| Setting               | Description                                                         | Mandatory |
| --------------------- | ------------------------------------------------------------------- | --------- |
| ExchangeConnectionUri | The connection URI to the Exchange On-Premises server               | Yes       |
| ExchangeAdminUsername | The username of the service account with Exchange management rights | Yes       |
| ExchangeAdminPassword | The password of the service account                                 | Yes       |

## Remarks

### Primary Email Address Cannot Be Removed Directly

- The form only displays secondary email addresses (smtp:) and excludes the primary SMTP address (SMTP:). To remove the current primary email address, you must first change it to a different email address using the "Change Primary Email Address" connector, then remove the old address as a secondary address.

### ExchangeGuid-Based Identification

- The connector uses ExchangeGuid as the unique identifier for mailboxes instead of UserPrincipalName or other attributes. This ensures reliable mailbox identification even when other attributes change.

### Wildcard Search Support

- The search functionality supports wildcard searches across multiple attributes: Name, SamAccountName, Alias, and PrimarySmtpAddress. Using "\*" as the search value will return all user mailboxes (limited by result size settings).

### TLS 1.2 Requirement

- The connector enforces TLS 1.2 for secure communications. Ensure your Exchange server and HelloID agent support TLS 1.2.

### Session Management

- Each datasource and task establishes its own Exchange remote session and properly cleans up the session after execution, even in error scenarios. This prevents session leaks and connection pool exhaustion.

## Development resources

### API documentation

- [Exchange PowerShell - Get-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/get-mailbox)
- [Exchange PowerShell - Set-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/set-mailbox)
- [Connect to Exchange Servers using remote PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-servers-using-remote-powershell)

## Getting help

> :bulb: **Tip:**  
> _For more information on Delegated Forms, please refer to our [documentation](https://docs.helloid.com/en/service-automation/delegated-forms.html) pages_.

## HelloID docs

The official HelloID documentation can be found at: https://docs.helloid.com/
