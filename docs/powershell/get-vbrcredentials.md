---
title: "Get-VBRCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcredentials.html"
last_updated: "4/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCredentials

In this article

Short Description

Returns credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get credentials records by specifying an array of user names.

|  |
| --- |
| Get-VBRCredentials [-Name <String[]>]  [<CommonParameters>] |

* Get credentials records by specifying an array of hosts.

|  |
| --- |
| Get-VBRCredentials [-Name <String[]>] [-Entity <Object[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns credentials records managed by Veeam Backup & Replication. You can get the list of all credentials records or look for instances directly by name.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of user names. The cmdlet will return credentials with these names. | String[] | False | Named | False |
| Entity | Specifies an array of hosts. The cmdlet will return credentials of these hosts. | Object[] | False | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CCredentials object that contains user credentials.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Credentials Records by Name

|  |  |
| --- | --- |
| This command gets credentials records with the Administrator user name.  |  | | --- | | Get-VBRCredentials -Name \*Administrator\* | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Credentials Records by Host

|  |  |
| --- | --- |
| This command gets credentials records of a specific host.  |  | | --- | | $host = Get-VBRServer  Get-VBRCredentials -Entity $host[1] |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $host variable. 2. Run the Get-VBRCredentials cmdlet. Set the $host variable as the Entity parameter value. Specify the necessary host of the $host variable. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 4/12/2024

Page content applies to build 13.0.1.1071
