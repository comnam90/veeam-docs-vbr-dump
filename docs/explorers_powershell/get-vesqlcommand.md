---
title: "get-vesqlcommand"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlcommand.html"
last_updated: "5/30/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns a set of cmdlets available for Veeam Explorer for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Veeam Explorer for Microsoft SQL Server cmdlets.

|  |
| --- |
| Get-VESQLCommand [<CommonParameters>] |

* Get a cmdlet with a specified name.

|  |
| --- |
| Get-VESQLCommand [[-Name] <String>] [<CommonParameters>] |

* Get cmdlets whose names contain a specified noun or verb.

|  |
| --- |
| Get-VESQLCommand [-Noun <String>] [-Verb <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of cmdlets available for Veeam Explorer for Microsoft SQL Server. You can query the cmdlets by the full name of the necessary cmdlet, or by the verb or noun in the cmdlet name.

For example, the Get-VESQLCommand cmdlet consists of the Get verb and the VESQLCommand noun. To get this cmdlet, you can search for it either by its full name, the Get verb or the VESQLCommand noun.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name to query cmdlets. The Get-VESQLCommand cmdlet will return a cmdlet whose name matches the specified name. | String | False | 0 | True (By |
| Noun | Specifies a noun to query cmdlets. The Get-VESQLCommand cmdlet will return a list of cmdlets whose names contain the specified noun. | String | False | Named | True (By Property Name) |
| Verb | Specifies a verb to query cmdlets. The Get-VESQLCommand cmdlet will return a list of cmdlets whose names contain the specified verb. | String | False | Named | True (By Property Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Veeam Explorer for Microsoft SQL Server PowerShell Cmdlets

|  |  |
| --- | --- |
| This command returns all Veeam Explorer for Microsoft SQL Server PowerShell cmdlets:  |  | | --- | | Get-VESQLCommand | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cmdlet with Specific Name

|  |  |
| --- | --- |
| This command returns the Get-VESQLDatabase cmdlet:  |  | | --- | | Get-VESQLCommand -Name Get-VESQLDatabase | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cmdlets that Contain Specific Verb

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the Get verb:  |  | | --- | | Get-VESQLCommand -Verb Get | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Cmdlets that Contain Specific Noun

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the VESQLDatabase noun:  |  | | --- | | Get-VESQLCommand -Noun VESQLDatabase | |

Page updated 5/30/2024

Page content applies to build 13.0.1.1071
