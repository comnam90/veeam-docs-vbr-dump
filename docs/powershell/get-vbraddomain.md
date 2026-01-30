---
title: "Get-VBRADDomain"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbraddomain.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Get-VBRADDomain


Short Description

Creates an object for connecting to Active Directory domain.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRADDomain -ServerName <String> [-Port <Int32>] -Credentials <CCredentials> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRADDomain](vbraddomain.md) object for connecting to the Active Directory domain. Veeam Backup & Replication will use this object to access Active Directory objects that you want to add to the scope of a protection group.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ServerName | Specifies the name for connecting to DC server/domain:   * DNS name for DC server * FQDN or NetBIOS for domain | String | True | Named | True (ByValue, ByProperty Name) |
| Port | Specifies the port for authenticating with the DC server/Domain.  Default: 389. | Int32 | False | Named | True (ByProperty Name) |
| Credentials | Specifies credentials for authenticating with DC server/Domain.  Note: for string type, enter a user name in the DNS.DOMAIN.NAME\USERNAME or USERNAME@DNS.DOMAIN.NAME format. | Accepts string (user name) or the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |
| Force | Defines that the cmdlet will make Veeam Backup & Replication trust the provided TLS and root certificates in the certificate chain without showing warnings in the PowerShell console. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRADDomain](vbraddomain.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Active Directory Domain Connection Object

|  |  |
| --- | --- |
| This example shows how to create an Active Directory domain connection object using credentials.  |  | | --- | | $adcreds = Get-Credential  Get-VBRADDomain -Server support.north -Credentials $adcreds |  Perform the following steps:   1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Type the credentials you want to use for authenticating with the DC server or Active Directory domain. Save the result to the $adcreds variable. 2. Run the Get-VBRADDomain cmdlet. Specify the Server parameter value. Set the $adcreds variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Active Directory Domain Connection Object

|  |  |
| --- | --- |
| This command shows how to create an Active Directory domain connection object using credentials in the DNS.DOMAIN.NAME\USERNAME format.  |  | | --- | | Get-VBRADDomain -Server support.north -Credentials tech.local\jsmith | |

Related Commands

* [Find-VBRADEntity](find-vbradentity.md)
* [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4)


