---
title: "New-VEPSQLInstanceCredentials"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new-vepsqlinstancecredentials.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VEPSQLInstanceCredentials


Short Description

Creates a PostgreSQL credential object to authenticate to a PostgreSQL database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create credentials using the current Linux OS user for PostgreSQL authentication.

|  |
| --- |
| New-VEPSQLInstanceCredentials [-UseLinuxUserForPeerAuthentication] [<CommonParameters>] |

* Create credentials specifying a particular Linux OS user for PostgreSQL peer authentication.

|  |
| --- |
| New-VEPSQLInstanceCredentials -PeerAuthenticationUser <String> [<CommonParameters>] |

* Create credentials using SQL username and password for PostgreSQL password authentication.

|  |
| --- |
| New-VEPSQLInstanceCredentials -SQLCredentials <PSCredential> [<CommonParameters>] |

Detailed Description

This cmdlet creates a [VEPSQLInstanceCredentials](vepsqlinstancecredentials.md) object that specifies authentication credentials for a PostgreSQL database. Use the resulting object with the [Start-VEPSQLDatabaseRestore](start-vepsqldatabaserestore.md) cmdlet to restore a PostgreSQL database.

You can define one of the following PostgreSQL authentication methods:

* Authentication using the current Linux OS user. PostgreSQL authenticates the client as the PostgreSQL role with the same name as the current Linux OS user. This works for peer authentication and also for password authentication if the password of the Linux OS user is the same as the password of the PostgreSQL role.
* Peer authentication using a specified Linux OS user. PostgreSQL authenticates the client as the PostgreSQL role mapped to the specified Linux OS user in the ident map file (pg\_ident.conf).
* Password authentication using a SQL username and password.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| UseLinuxUserForPeerAuthentication | Defines that the cmdlet will use the current Linux OS user for PostgreSQL authentication. PostgreSQL will authenticate the client as the PostgreSQL role with the same name as the current Linux OS user.  This works for peer authentication and also for password authentication if the password of the Linux OS user is the same as the password of the PostgreSQL role. | SwitchParameter | True | Named | False |
| PeerAuthenticationUser | Specifies the name of the Linux OS user for PostgreSQL peer authentication.  PostgreSQL will authenticate the client as the PostgreSQL role mapped to the specified Linux OS user in the ident map file (pg\_ident.conf). | String | True | Named | False |
| SQLCredentials | Specifies SQL credentials for PostgreSQL password authentication. The cmdlet will use these credentials to authenticate to the PostgreSQL database. | Accepts the PSCredential object. To create this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstanceCredentials](vepsqlinstancecredentials.md) object that contains PostgreSQL authentication credentials.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Credentials for Current Linux User Peer Authentication

|  |  |
| --- | --- |
| This command creates a PostgreSQL credentials object using the current Linux OS user for peer authentication. Save the result to the $creds variable to use it with other cmdlets.  |  | | --- | | $creds = New-VEPSQLInstanceCredentials -UseLinuxUserForPeerAuthentication | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Credentials for Specified Linux User Peer Authentication

|  |  |
| --- | --- |
| This command creates a PostgreSQL credentials object using a specified Linux OS user for peer authentication. Save the result to the $creds variable to use it with other cmdlets.  |  | | --- | | $creds = New-VEPSQLInstanceCredentials -PeerAuthenticationUser "wells" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Credentials with SQL Username and Password

|  |  |
| --- | --- |
| This example shows how to create a PostgreSQL credentials object using SQL username and password for password authentication.  |  | | --- | | $sqlcred = Get-Credential  $creds = New-VEPSQLInstanceCredentials -SQLCredentials $sqlcred |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter the PostgreSQL credentials that will be used for authentication. Save the result to the $sqlcred variable. 2. Run the New-VEPSQLInstanceCredentials cmdlet. Set the $sqlcred variable as the SQLCredentials parameter value. Save the result to the $creds variable to use it with other cmdlets. |

Related Commands

[Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

Page updated 2026-06-25

