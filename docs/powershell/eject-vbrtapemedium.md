---
title: "Eject-VBRTapeMedium"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/eject-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Eject-VBRTapeMedium

In this article

Short Description

Ejects tapes from drive.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Eject tapes in all drives.

|  |
| --- |
| Eject-VBRTapeMedium  [<CommonParameters>] |

* Eject a selected tape.

|  |
| --- |
| Eject-VBRTapeMedium -Medium <VBRTapeMedium[]>  [<CommonParameters>] |

* Eject a tape located in a selected drive.

|  |
| --- |
| Eject-VBRTapeMedium -Drive <VBRTapeDrive[]>  [<CommonParameters>] |

Detailed Description

This cmdlet ejects the tape that is located in drive. The ejected tape is moved to a standard library slot.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the array of tapes. The cmdlet will eject these tapes. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Drive | Specifies the array of drives. The cmdlet will eject tapes from these drives. | Accepts the [VBRTapeDrive[]](vbrtapedrive.md) object, GUID or string. To get this object, run the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Ejecting Selected Tape

This example shows how to eject tape named 00140009.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "00140009"  Eject-VBRTapeMedium -Medium $tape |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save it to the $tape variable.
2. Run the Eject-VBRTapeMedium cmdlet. Set the $tape variable as the Medium parameter value.

Related Commands

* [Get-VBRTapeMedium](get-vbrtapemedium.md)
* [Get-VBRTapeDrive](get-vbrtapedrive.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
