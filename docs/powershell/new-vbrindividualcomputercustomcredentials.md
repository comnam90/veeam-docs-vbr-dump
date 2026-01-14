---
title: "New-VBRIndividualComputerCustomCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrindividualcomputercustomcredentials.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# New-VBRIndividualComputerCustomCredentials

In this article

Short Description

Specifies a method for authenticating individual computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Specify username and password.

|  |
| --- |
| New-VBRIndividualComputerCustomCredentials -HostName <String> -Credentials <CCredentials>  [<CommonParameters>] |

* Specify a temporary certificate.

|  |
| --- |
| New-VBRIndividualComputerCustomCredentials -HostName <String> [-UseTemporaryCertificate]  [<CommonParameters>] |

* Specify temporary credentials.

|  |
| --- |
| New-VBRIndividualComputerCustomCredentials -HostName <String> [-SSHTempCredentials] -SSHUser <String> -SSHPassword <String> [-SSHPort <UInt16>] [-SSHElevateToRoot] [-SSHFailoverToSu] [-SSHRootPassword <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet specifies a method for authenticating individual computers that you want to add to a protection group. Veeam Backup & Replication uses this method for Veeam Agent deployment and backup\restore activities.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| HostName | Specifies the DNS name or an IP address of the computer for which you want to specify custom credentials. | String | True | Named | True (ByValue, ByProperty Name) |
| Credentials | Specifies a method to authenticate against individual computers in a protection group.  Note: for string type, enter a user name in the DNS.DOMAIN.NAME\USERNAME or USERNAME@DNS.DOMAIN.NAME format. | Accepts string (user name) or the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | True (ByProperty Name) |
| SSHPassword | Specifies the password you want to use to authenticate against individual computers in a protection group. | String | True | Named | True (ByProperty Name) |
| UseTemporaryCertificate | Defines that the cmdlet will use temporary certificate. | SwitchParameter | True | Named | True (ByProperty Name) |
| SSHUser | Specifies the user name you want to use to authenticate against individual computers in a protection group. | String | True | Named | True (ByProperty Name) |
| SSHTempCredentials | Defines that the cmdlet will use single-use credentials to access Linux-based machines. | SwitchParameter | True | Named | True (ByProperty Name) |
| SSHElevateToRoot | Defines that the cmdlet will grant the non-root users with root account privileges. | SwitchParameter | False | Named | True (ByProperty Name) |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails. | SwitchParameter | False | Named | True (ByProperty Name) |
| SSHPort | Specifies the Web service port to connect to Linux-based machines.  Default: 443. | UInt16 | False | Named | True (ByProperty Name) |
| SSHRootPassword | Specifies the root password used for authentication. | String | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRIndividualComputerCustomCredentials](vbrindividualcomputercustomcredentials.md) object that contains a method for authenticating individual computers.

Examples

Specifying Credentials for Authenticating with Individual Computers

This example shows how to specify credentials for authenticating individual computers.

|  |
| --- |
| $ccreds = Get-Credential  New-VBRIndividualComputerCustomCredentials -HostName 172.19.51.50 -Credentials $creds |

Perform the following steps:

1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Type the credentials and save the result to the $ccreds variable.
2. Run the New-VBRIndividualComputerCustomCredentials cmdlet. Specify the HostName parameter value. Set the $ccreds variable as the Credentials parameter value.

Related Commands

[New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md)

Page updated 7/31/2025

Page content applies to build 13.0.1.1071
