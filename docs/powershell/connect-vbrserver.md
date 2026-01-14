---
title: "Connect-VBRServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrserver.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Connect-VBRServer

In this article

Short Description

Connects to a Veeam backup server.

Syntax

This cmdlet provides parameter sets that allow you to:

* Connect to a Veeam backup server as a current user.

|  |
| --- |
| Connect-VBRServer [-Server <String>] [-Port <Int32>] [-Timeout <Int32>] [-ForceAcceptTlsCertificate]  [<CommonParameters>] |

* Connect to a Veeam backup server using User/Password authentication.

|  |
| --- |
| Connect-VBRServer [-Server <String>] [-Port <Int32>] -User <String> -Password <String> [-Timeout <Int32>] [-ForceAcceptTlsCertificate] [<CommonParameters>] |

* Connect to a Veeam backup server using using the credentials prompt.

|  |
| --- |
| Connect-VBRServer [-Server <String>] [-Port <Int32>] -Credential <PSCredential> [-Timeout <Int32>] [-ForceAcceptTlsCertificate] [<CommonParameters>] |

Detailed Description

This cmdlet creates connection with a local or remote Veeam backup server. The connection starts a Veeam PowerShell session during which you can perform all operations available with Veeam PowerShell.

If you do not specify the server, you will connect to the local Veeam backup server.

|  |
| --- |
| Note |
| Only local and domain user accounts can be used for authentication. User accounts with SAML authentication are not supported. |

Within one PowerShell session, you can connect to one Veeam server. To connect to another Veeam server, you need to close the current session.

Run the [Disconnect-VBRServer](disconnect-vbrserver.md) cmdlet to stop session with the current Veeam server.

Run the [Get-VBRServerSession](get-vbrserversession.md) cmdlet to get information about the current session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the Veeam server to which you want to connect.  Default: localhost. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Port | Specifies the port for connection.  Default: 9392. | Int | False | Named | False |
| Timeout | Specifies timeout for waiting for a blocked session. | Int32 | False | Named | False |
| ForceAcceptTlsCertificate | Defines that the cmdlet will accept the backup server TLS certificate. | SwitchParameter | False | Named | False |
| User | Specifies the user name you want to use for authenticating with the remote server.  Note: You must specify the user name in the DOMAIN\Username or UPN format. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the Veeam server. | String | True | Named | False |
| Credential | Specifies the credentials you want to use for authenticating with the Veeam server.  Note: When creating the PSCredential object, you must specify the user name in the DOMAIN\Username or UPN format. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Connecting to Veeam Backup Server as Current User

|  |  |
| --- | --- |
| This command connects to the 192.24.125.135 Veeam backup server as a current user.  |  | | --- | | Connect-VBRServer -Server 192.24.125.135 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Connecting to Veeam Backup Server with User/Password Authentication

|  |  |
| --- | --- |
| This command connects to the 192.24.125.135 server using the User/Password authentication.  |  | | --- | | Connect-VBRServer -Server "192.24.125.135" -User "TECH\Administrator" -Password "Password" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Connecting to Veeam Backup Server Using Credentials Prompt

|  |  |
| --- | --- |
| This example shows how to connect to the 192.24.125.135 Veeam backup server using the credentials prompt.  |  | | --- | | $creds = Get-Credential  Connect-VBRServer -Credential $creds -Server 192.24.125.135 |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. The cmdlet will prompt for a user name and password. Enter the necessary values. Save the result to the $creds variable. 2. Run the Connect-VBRServer cmdlet. Set the $creds variable as the Credential parameter value. Specify the Server parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRLocalhost](get-vbrlocalhost.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1)

Page updated 10/17/2025

Page content applies to build 13.0.1.1071
