---
title: "Get-VBRRecoveryMediaTarget"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrecoverymediatarget.html"
last_updated: "10/9/2025"
product_version: "13.0.1.1071"
---

# Get-VBRRecoveryMediaTarget


Short Description

Returns available bootable media for creating Veeam Recovery Media.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all available bootable media.

|  |
| --- |
| Get-VBRRecoveryMediaTarget [<CommonParameters>] |

* Get available bootable media by name.

|  |
| --- |
| Get-VBRRecoveryMediaTarget [-Name <String[]>] [<CommonParameters>] |

* Get available bootable media by type (RemovableDevice/ISO).

|  |
| --- |
| Get-VBRRecoveryMediaTarget [-Type <VBRRecoveryMediaType[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns available bootable media for creating Veeam Recovery Media. You can get the list of all media or search for instances directly by name or type.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of bootable media names. The cmdlet will return available bootable media with these names. | String[] | False | Named | True (ByProperty Name) |
| Type | Specifies the array of bootable media types. The cmdlet will return available bootable media. | VBRRecoveryMediaType[] | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRRecoveryMediaTarget[] object that contains an array of available bootable media for creating Veeam Recovery Media.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Available Bootable Media

|  |  |
| --- | --- |
| This command returns all available bootable media.  |  | | --- | | Get-VBRRecoveryMediaTarget | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Removable Bootable Media

|  |  |
| --- | --- |
| This command returns all attached removable storage devices that can be used for creating Veeam Recovery Media.  |  | | --- | | Get-VBRRecoveryMediaTarget -Type RemovableDevice | |


