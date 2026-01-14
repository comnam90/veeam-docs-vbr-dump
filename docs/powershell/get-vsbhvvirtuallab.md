---
title: "Get-VSBHvVirtualLab (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vsbhvvirtuallab.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VSBHvVirtualLab (obsolete)

In this article

Short Description

Returns Hyper-V virtual labs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides 2 parameter sets.

* For getting Hyper-V virtual labs by name:

|  |
| --- |
| Get-VSBHvVirtualLab [-Name <string[]>]  [<CommonParameters>] |

* For getting Hyper-V virtual labs by ID:

|  |
| --- |
| Get-VSBHvVirtualLab [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Hyper-V virtual labs that are connected to the Veeam backup console.

Run the [Find-VSBHvVirtualLab](find-vsbhvvirtuallab.md) cmdlet to look for virtual labs that are not managed by Veeam Backup & Replication.

You can get the list of all virtual labs or search for instances directly by name or ID.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of Hyper-V virtual lab names. The cmdlet will return Hyper-V virtual labs with these names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Id | Specifies the array of Hyper-V virtual lab IDs. The cmdlet will return Hyper-V virtual labs with these IDs. | Accepts GUID or string. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Virtual Labs

|  |  |
| --- | --- |
| This command returns the list of all virtual labs created or connected to Veeam Backup & Replication.  |  | | --- | | Get-VSBHvVirtualLab | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Labs by Name

|  |  |
| --- | --- |
| This command returns the list of virtual labs with names starting with Exchange.  |  | | --- | | Get-VSBHvVirtualLab -Name Exchange\* | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Virtual Labs by Id

|  |  |
| --- | --- |
| This command returns virtual labs by Id.  |  | | --- | | Get-VSBVirtualLab -Id 1022504c-9008-4883-b166-718bdf7280ea, 502dc485-84f5-4a9d-86e7-8b00d1d5a0be | |

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
