---
title: "Get-VEMDBCommand"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbcommand.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Get-VEMDBCommand


Short Description

Returns a set of cmdlets available for Veeam Explorer for MongoDB.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cmdlets for Veeam Explorer for MongoDB.

|  |
| --- |
| Get-VEMDBCommand [<CommonParameters>] |

* Get a cmdlet with a specific name.

|  |
| --- |
| Get-VEMDBCommand [[-Name] <String>] [<CommonParameters>] |

* Get cmdlets whose names contain the specified noun or verb.

|  |
| --- |
| Get-VEMDBCommand [-Noun <String>] [-Verb <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of cmdlets available for Veeam Explorer for MongoDB. You can query the cmdlets by the full name of the necessary cmdlet, or by the verb or noun in the cmdlet name.

For example, the Get-VEMDBCommand cmdlet consists of the Get verb and the VEMDBCommand noun. To get this cmdlet, you can search for it either by its full name, the Get verb or the VEMDBCommand noun.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name to query cmdlets. The Get-VEMDBCommand cmdlet will return a cmdlet whose name matches the specified name. | String | False | 0 | True (ByValue, |
| Noun | Specifies a noun to query cmdlets. The Get-VEMDBCommand cmdlet will return a list of cmdlets whose names contain the specified noun. | String | False | Named | True (By Property Name) |
| Verb | Specifies a verb to query cmdlets. The Get-VEMDBCommand cmdlet will return a list of cmdlets whose names contain the specified verb. | String | False | Named | True (By Property Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cmdlets for Veeam Explorer for MongoDB

|  |  |
| --- | --- |
| This command returns all cmdlets for Veeam Explorer for MongoDB:  |  | | --- | | Get-VEMDBCommand | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cmdlet with Specific Name

|  |  |
| --- | --- |
| This command returns the Get-VEMDBDatabase cmdlet:  |  | | --- | | Get-VEMDBCommand -Name Get-VEMDBDatabase | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cmdlets that Contain Specific Verb

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the Get verb:  |  | | --- | | Get-VEMDBCommand -Verb Get | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Cmdlets that Contain Specific Noun

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the VEMDBDatabase noun:  |  | | --- | | Get-VEMDBCommand -Noun VEMDBDatabase | |


