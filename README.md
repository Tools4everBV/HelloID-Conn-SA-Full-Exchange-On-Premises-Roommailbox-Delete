# HelloID-Conn-SA-Full-Exchange-On-Premises-Roommailbox-Delete

| :information_source: Information                                                                                                                                                                                                                                                                                                                                                          |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| This repository contains the connector and configuration code only. The implementer is responsible for acquiring the connection details such as username, password, certificate, etc. You might even need to sign a contract or agreement with the supplier before implementing this connector. Please contact the client's application manager to coordinate the connector requirements. |

## Description

_HelloID-Conn-SA-Full-Exchange-On-Premises-Roommailbox-Delete_ is a template designed for use with HelloID Service Automation (SA) Delegated Forms. It can be imported into HelloID and customized according to your requirements.

By using this delegated form, you can efficiently manage Exchange On-Premises room mailboxes. The following options are available:

1.  Search for room mailboxes by name, alias, or primary SMTP address
2.  Select the room mailbox to delete from a grid view
3.  Delete the selected room mailbox
4.  Comprehensive audit logging of all actions

## Getting started

### Requirements

- **Exchange On-Premises Environment**:<br>
  An Exchange On-Premises server with PowerShell remoting enabled. The server must be accessible via the Exchange Management Shell remote PowerShell endpoint.
- **Administrative Credentials**:<br>
  A service account with sufficient permissions to query and remove room mailboxes in Exchange On-Premises. The account must have the necessary Exchange RBAC roles assigned.
- **TLS 1.2**:<br>
  TLS 1.2 must be enabled on both the HelloID agent/runner and the Exchange server to ensure secure communication.
- **Network Connectivity**:<br>
  The HelloID agent must be able to establish a PowerShell remoting session to the Exchange On-Premises server on the configured connection URI.

### Connection settings

The following user-defined variables are used by the connector.

| Setting               | Description                                                                 | Mandatory |
| --------------------- | --------------------------------------------------------------------------- | --------- |
| ExchangeConnectionUri | The PowerShell connection URI to the Exchange On-Premises server            | Yes       |
| ExchangeAdminUsername | The username of the service account with Exchange administrative privileges | Yes       |
| ExchangeAdminPassword | The password of the service account                                         | Yes       |

## Remarks

### Room Mailbox Deletion is Permanent

- **Irreversible Action**: Deleting a room mailbox is a permanent action. The mailbox and all associated data will be removed from Exchange. Ensure proper confirmation workflows are in place before allowing users to delete room mailboxes.

### PowerShell Remoting Requirements

- **Remote PowerShell**: This connector uses PowerShell remoting to connect to Exchange On-Premises. Ensure that PowerShell remoting is properly configured on the Exchange server and that the service account has the necessary permissions to establish remote sessions.

### Session Management

- **Connection Cleanup**: The connector automatically disconnects and cleans up PowerShell sessions after each operation to prevent resource leaks and session exhaustion on the Exchange server.

### Wildcard Search Filtering

- **Search Performance**: The datasource uses wildcard filtering on Name, Alias, and PrimarySmtpAddress properties. For large Exchange environments, consider implementing additional filters or limiting result sets to improve performance.

## Development resources

### PowerShell Cmdlets

The following Exchange PowerShell cmdlets are used by the connector:

| Cmdlet         | Description                                                 |
| -------------- | ----------------------------------------------------------- |
| Get-Mailbox    | Retrieves room mailbox information for search and selection |
| Remove-Mailbox | Deletes the selected room mailbox                           |

### API documentation

- [Connect to Exchange servers using remote PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-servers-using-remote-powershell)
- [Get-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/get-mailbox)
- [Remove-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/remove-mailbox)

## Getting help

> :bulb: **Tip:**  
> _For more information on Delegated Forms, please refer to our [documentation](https://docs.helloid.com/en/service-automation/delegated-forms.html) pages_.

## HelloID docs

The official HelloID documentation can be found at: https://docs.helloid.com/
