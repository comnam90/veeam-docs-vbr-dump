---
title: "Import-VBRTapeMedium"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Import-VBRTapeMedium

In this article

Short Description

Imports tapes into library.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Import-VBRTapeMedium -Library <VBRTapeLibrary[]> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet imports tapes newly loaded to a tape library.

You need to run importing procedure against all new tapes. Importing moves tapes from I/E slot to library standard slots.

|  |
| --- |
| ![Import-VBRTapeMedium](images/icon_note.webp) Note: |
| Import and export commands are available only for the devices that support corresponding operations and include I/E slot. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Library | Specifies the library from which you want to import tapes. | Accepts the [VBRTapeLibrary[]](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Wait | Defines that the command waits for the import sessions to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupSession](vbrbackupsession.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Importing Tapes into Tape Library

|  |  |
| --- | --- |
| This example shows how to import tapes to the HP MSL G3 Series 3.00 tape library.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Import-VBRTapeMedium |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Import-VBRTapeMedium cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Importing Tapes into Tape Library [Using Variable]

|  |  |
| --- | --- |
| This example shows how to import tapes to the HP MSL G3 Series 3.00 tape library.  |  | | --- | | $library = Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00"  Import-VBRTapeMedium -Library $library |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save the result to the $library variable. 2. Run the Get-VBRTapeLibrary cmdlet. Set the $library variable as the Library parameter value. |

Related Commands

[Get-VBRTapeLibrary](get-vbrtapelibrary.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
