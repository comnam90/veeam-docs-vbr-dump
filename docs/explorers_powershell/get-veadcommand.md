---
title: "get-veadcommand"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veadcommand.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns a set of cmdlets available for Veeam Explorer for Microsoft Active Directory.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Veeam Explorer for Microsoft Active Directory cmdlets.

|  |
| --- |
| Get-VEADCommand [<CommonParameters>] |

* Get a cmdlet with a specified name.

|  |
| --- |
| Get-VEADCommand [[-Name] <string>] [<CommonParameters>] |

* Get cmdlets whose names contain a specified noun or verb.

|  |
| --- |
| Get-VEADCommand [-Noun <string>] [-Verb <string>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of cmdlets available for Veeam Explorer for Microsoft Active Directory. You can query the cmdlets by the full name of the necessary cmdlet, or by the verb or noun in the cmdlet name.

For example, the Get-VEADCommand cmdlet consists of the Get verb and the VEADCommand noun. To get this cmdlet, you can search for it either by its full name, the Get verb or the VEADCommand noun.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name to query cmdlets. The Get-VEADCommand cmdlet will return a cmdlet whose name matches the specified name. | String | False | 0 | True (ByValue, |
| Noun | Specifies a noun to query cmdlets. The Get-VEADCommand cmdlet will return a list of cmdlets whose names contain the specified noun. | String | False | Named | True (By Property Name) |
| Verb | Specifies a verb to query cmdlets. The Get-VEADCommand cmdlet will return a list of cmdlets whose names contain the specified verb. | String | False | Named | True (By Property Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Veeam Explorer for Microsoft Active Directory PowerShell Cmdlets

|  |  |
| --- | --- |
| This command returns all PowerShell cmdlets for Veeam Explorer for Microsoft Active Directory.  |  | | --- | | Get-VEADCommand | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cmdlet with Specific Name

|  |  |
| --- | --- |
| This command returns a cmdlet with the Get-VEADItem name.  |  | | --- | | Get-VEADCommand -Name Get-VEADItem | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cmdlets that Contain Specific Verb

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the Get verb.  |  | | --- | | Get-VEADCommand -Verb Get | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Cmdlets that Contain Specific Noun

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the VEADItem noun.  |  | | --- | | Get-VEADCommand -Noun VEADItem | |

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
