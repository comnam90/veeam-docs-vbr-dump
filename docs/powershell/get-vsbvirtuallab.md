---
title: "Get-VSBVirtualLab (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vsbvirtuallab.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VSBVirtualLab (obsolete)


Short Description

Returns VMware virtual labs.

|  |
| --- |
| ![Get-VSBVirtualLab (obsolete)](images/icon_note.webp) Note: |
| This cmdlet is deprecated and will be marked as obsolete in the future. It is recommended to re-write your scripts using the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. |

Applies to

Platform: VMware

For Hyper-V, run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet.

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides 2 parameter sets.

* For getting VMware virtual labs by name:

|  |
| --- |
| Get-VSBVirtualLab [-Name <string[]>]  [<CommonParameters>] |

* For getting VMware virtual labs by ID:

|  |
| --- |
| Get-VSBVirtualLab [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing VMware virtual labs.

Run the [Find-VSBVirtualLab](find-vsbvirtuallab.md) cmdlet to look for virtual labs that are not managed by Veeam Backup & Replication.

You can get the list of all virtual labs or search for instances directly by name or ID.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of VMware virtual lab names. The cmdlet will return VMware virtual labs with these names. | String[] | False | Named | False |
| Id | Specifies the array of VMware virtual lab IDs. The cmdlet will return VMware virtual labs with these IDs. | Accepts GUID or string. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Virtual Labs

|  |  |
| --- | --- |
| This command returns the list of all virtual labs.  |  | | --- | | Get-VSBVirtualLab | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Labs by Name

|  |  |
| --- | --- |
| This command returns virtual labs by name.  |  | | --- | | Get-VSBVirtualLab -Name "MailServer VLab 01", "MailServer VLab 05" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Virtual Labs by Id

|  |  |
| --- | --- |
| This command returns virtual labs by Id.  |  | | --- | | Get-VSBVirtualLab -Id 3fw1505l-8811-4283-b066-718bdf7280ea, 909fg28c-14f5-9a9d-6ve7-0b40d1k5a9jm | |


