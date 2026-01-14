---
title: "Eject-VBRTapeDrive (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/eject-vbrtapedrive.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Eject-VBRTapeDrive (obsolete)

In this article

Short Description

Ejects tape from the selected media drive.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to rewrite your scripts using the [Eject-VBRTapeMedium](eject-vbrtapemedium.md) cmdlet. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Eject-VBRTapeDrive -Drive <TapeDrive> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet ejects tape from the specified drive. The tape returns to its original slot.

Run the Eject-VBRTapeMedium cmdlet to eject a specific tape from drive.

Run the [Export-VBRTapeMedium](export-vbrtapemedium.md) cmdlet to get a tape out of the library.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Drive | Specifies the drive you want to eject. | Accepts the TapeDrive object. To get this object, run the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Ejecting Tape from Drive [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to eject the tape from the Drive01 drive.  |  | | --- | | Get-VBRTapeDrive -Name "Drive01" | Eject-VBRTapeDrive |  Perform the following steps:   1. Run the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Eject-VBRTapeDrive cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Ejecting Tape from Drive [Using Variable]

|  |  |
| --- | --- |
| This example shows how to eject the tape from the Drive01 drive.  |  | | --- | | $drive = Get-VBRTapeDrive -Name "Drive01"  Eject-VBRTapeDrive -Drive $drive |  Perform the following steps:   1. Run the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. Specify the Name parameter value. Save the result to the $drive variable. 2. Pipe the cmdlet output to the Eject-VBRTapeDrive cmdlet. Set the $drive variable as the Drive parameter value. |

Related Commands

[Get-VBRTapeDrive](get-vbrtapedrive.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
