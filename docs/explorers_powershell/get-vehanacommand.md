---
title: "Get-VEHANACommand"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanacommand.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Get-VEHANACommand


Short Description

Returns a set of cmdlets available for Veeam Explorer for SAP HANA.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cmdlets for Veeam Explorer for SAP HANA.

|  |
| --- |
| Get-VEHANACommand [<CommonParameters>] |

* Get a cmdlet with a specific name.

|  |
| --- |
| Get-VEHANACommand [[-Name] <string>] [<CommonParameters>] |

* Get cmdlets whose names contain the specified noun or verb.

|  |
| --- |
| Get-VEHANACommand [-Noun <string>] [-Verb <string>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of cmdlets available for Veeam Explorer for SAP HANA. You can query the cmdlets by the full name of the necessary cmdlet, or by the verb or noun in the cmdlet name.

For example, the Get-VEHANACommand cmdlet consists of the Get verb and the VEHANACommand noun. To get this cmdlet, you can search for it either by its full name, the Get verb or the VEHANACommand noun.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name to query cmdlets. The Get-VEHANACommand cmdlet will return a cmdlet whose name matches the specified name. | String | False | 0 | True (ByValue, |
| Noun | Specifies a noun to query cmdlets. The Get-VEHANACommand cmdlet will return a list of cmdlets whose names contain the specified noun. | String | False | Named | True (By Property Name) |
| Verb | Specifies a verb to query cmdlets. The Get-VEHANACommand cmdlet will return a list of cmdlets whose names contain the specified verb. | String | False | Named | True (By Property Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cmdlets for Veeam Explorer for SAP HANA

|  |  |
| --- | --- |
| This command returns all cmdlets for Veeam Explorer for SAP HANA:  |  | | --- | | Get-VEHANACommand | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cmdlet with Specific Name

|  |  |
| --- | --- |
| This command returns the Get-VEHANADatabase cmdlet:  |  | | --- | | Get-VEHANACommand -Name Get-VEHANADatabase | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cmdlets that Contain Specific Verb

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the Get verb:  |  | | --- | | Get-VEHANACommand -Verb Get | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Cmdlets that Contain Specific Noun

|  |  |
| --- | --- |
| This command returns cmdlets whose names contain the VEHANADatabase noun:  |  | | --- | | Get-VEHANACommand -Noun VEHANADatabase | |


