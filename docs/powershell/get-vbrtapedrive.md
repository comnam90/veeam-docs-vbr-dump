---
title: "Get-VBRTapeDrive"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapedrive.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeDrive

In this article

Short Description

Returns tape drives.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all tape drives.

|  |
| --- |
| Get-VBRTapeDrive  [<CommonParameters>] |

* Get tape drives belonging to a specific library.

|  |
| --- |
| Get-VBRTapeDrive [-Library <VBRTapeLibrary>]  [<CommonParameters>] |

* Get tape drives by names.

|  |
| --- |
| Get-VBRTapeDrive [-Name <string[]>]  [<CommonParameters>] |

* Get tape drives by IDs.

|  |
| --- |
| Get-VBRTapeDrive [-Id <guid[]>]  [<CommonParameters>] |

* Get tape drives by slot numbers.

|  |
| --- |
| Get-VBRTapeDrive -Address <int[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns tape recording drives. You can also view the model name, the state of the drive and whether it is enabled or disabled.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Library | Specifies the tape library. The cmdlet will return drives that belong to this library. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of tape drive names. The cmdlet will return drives with these names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Id | Specifies the array of drive IDs. The cmdlet will return drives with these IDs. | Guid[] | False | Named | True (ByValue, ByProperty Name) |
| Address | Specifies the array of drive addresses (slot numbers). The cmdlet will return drives in these slots. | Int32[] | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeDrive[]](vbrtapedrive.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Drives of Selected Library [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get drives of the HP MSL G3 Series 3.00 library.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Get-VBRTapeDrive |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Drive by Name

|  |  |
| --- | --- |
| This command looks for the Drive1 tape drive.  |  | | --- | | Get-VBRTapeDrive -Name "Drive1" | |

Related Commands

[Get-VBRTapeLibrary](get-vbrtapelibrary.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
