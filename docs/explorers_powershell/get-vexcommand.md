---
title: "Get-VEXCommand"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexcommand.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Get-VEXCommand


Short Description

Returns a set of cmdlets available for Veeam Explorer for Microsoft Exchange.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Veeam Explorer for Microsoft Exchange cmdlets.

|  |
| --- |
| Get-VEXCommand [<CommonParameters>] |

* Get a cmdlet with a specified name.

|  |
| --- |
| Get-VEXCommand [[-Name] <String>] [<CommonParameters>] |

* Get cmdlets whose names contain a specified noun or verb.

|  |
| --- |
| Get-VEXCommand [-Noun <String>] [-Verb <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of cmdlets available for Veeam Explorer for Microsoft Exchange. You can query the cmdlets by the full name of the necessary cmdlet, or by the verb or noun in the cmdlet name.

For example, the Get-VEXCommand cmdlet consists of the Get verb and the VEXCommand noun. To get this cmdlet, you can search for it either by its full name, the Get verb or the VEXCommand noun.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name to query cmdlets. The cmdlet will return a cmdlet whose name matches the specified name. | String | False | 0 | True (ByValue, |
| Noun | Specifies a noun to query cmdlets. The cmdlet will return a list of cmdlets whose names contain the specified noun. | String | False | Named | True (By Property Name) |
| Verb | Specifies a verb to query cmdlets. The cmdlet will return a list of cmdlets whose names contain the specified verb. | String | False | Named | True (By Property Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Veeam Explorer for Microsoft Exchange PowerShell Cmdlets

|  |  |
| --- | --- |
| This command returns all Veeam Explorer for Microsoft Exchange PowerShell cmdlets.  |  | | --- | | Get-VEXCommand | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cmdlet by Name

|  |  |
| --- | --- |
| This command returns the Get-VEXItem cmdlet.  |  | | --- | | Get-VEXCommand -Name Get-VEXItem | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cmdlets by Verb

|  |  |
| --- | --- |
| This command returns a list of cmdlets whose names contain the Get verb.  |  | | --- | | Get-VEXCommand -Verb Get | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Cmdlets that Contain Specific Noun

|  |  |
| --- | --- |
| This command returns a list of cmdlets whose names contain the VEXItem noun.  |  | | --- | | Get-VEXCommand -Noun VEXItem | |


