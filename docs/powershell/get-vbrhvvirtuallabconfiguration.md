---
title: "Get-VBRHvVirtualLabConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrhvvirtuallabconfiguration.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRHvVirtualLabConfiguration


Short Description

Returns virtual labs and their settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all virtual labs that are added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Get-VBRHvVirtualLabConfiguration  [<CommonParameters>] |

* Get an array of virtual labs with the specified ID.

|  |
| --- |
| Get-VBRHvVirtualLabConfiguration [-Id <guid[]>]  [<CommonParameters>] |

* Get an array of virtual labs with the specified name.

|  |
| --- |
| Get-VBRHvVirtualLabConfiguration [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRHvVirtualLabConfiguration object that contains an array of virtual labs and all their settings. You can use this object to modify settings of virtual labs.

Run the [Set-VBRHvVirtualLab](set-vbrhvvirtuallab.md) cmdlet to modify settings of virtual labs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for a virtual lab. The cmdlet will return an array of virtual labs with the specified ID. | Guid[] | False | Named | False |
| Name | Specifies an array of names for a virtual lab. The cmdlet will return an array of virtual labs with the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvVirtualLabConfiguration object that an array of virtual labs and all their settings

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Virtual Labs

|  |  |
| --- | --- |
| This example shows how to get all virtual labs that are added to the backup infrastructure.  |  | | --- | | Get-VBRHvVirtualLabConfiguration | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Lab by ID

|  |  |
| --- | --- |
| This example shows how to get the virtual lab with 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec ID.  |  | | --- | | Get-VBRHvVirtualLabConfiguration -Id "6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Virtual Lab by Name

|  |  |
| --- | --- |
| This example shows how to get the virtual lab named SQL Virtual Lab.  |  | | --- | | Get-VBRHvVirtualLabConfiguration -Name "SQL Virtual Lab" | |


