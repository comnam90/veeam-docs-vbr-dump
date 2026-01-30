---
title: "New-VBRCSVCustomCredentials"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcsvcustomcredentials.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# New-VBRCSVCustomCredentials


Short Description

Specifies custom credentials for authenticating with computers listed in a CSV file.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRCSVCustomCredentials -HostName <string> [-Credentials <CCredentials>]  [<CommonParameters>] |

Detailed Description

This cmdlet specifies custom credentials for authenticating with computers you want to add to a protection group from a CSV file. Veeam Backup & Replication uses these credentials for Veeam Agent deployment and backup\restore activities.

By default, Veeam Backup & Replication uses Master account credentials for authenticating with all computers listed in a CSV file. For authenticating with computers that require different credentials Veeam Backup & Replication uses custom credentials.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| HostName | Specifies DNS-name or IP address of the computer for which you want to specify credentials. | String | True | Named | True (ByValue, ByProperty Name) |
| Credentials | Specifies custom credentials for authenticating with computers listed in a CSV file.  If not set, Veeam Backup & Replication will use Master account credentials for authenticating with associated computers.  Note: for string type, enter a user name in the DNS.DOMAIN.NAME\USERNAME or USERNAME@DNS.DOMAIN.NAME format. | Accepts string (user name) or the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCSVCustomCredentials](vbrcsvcustomcredentials.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Custom Credentials for Computers from CSV File

|  |  |
| --- | --- |
| This example shows how to specify custom credentials for computers from a CSV file.  |  | | --- | | $ccreds = Get-Credential  @("172.19.51.55", "sup-v8931") | ForEach { New-VBRCSVCustomCredentials -HostName $\_ -Credentials $ccreds} |  Perform the following steps:   1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) to create a credential object you want to use for authenticating with computers. Type the credentials and save the result to the $ccreds variable. 2. Run the New-VBRCSVCustomCredentials cmdlet. Set the $ccreds variable as the Credentials parameter value. Use the ForEach statement to apply the same credentials to multiple computers. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Master Credentials for Computers from CSV File

|  |  |
| --- | --- |
| This command specifies master credentials for the computer from a CSV file.  |  | | --- | | New-VBRCSVCustomCredentials -HostName 172.19.51.50 | |

Related Commands

[New-VBRCSVContainer](new-vbrcsvcontainer.md)


