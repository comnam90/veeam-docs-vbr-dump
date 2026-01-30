---
title: "Export-VBRTapeMedium"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Export-VBRTapeMedium


Short Description

Moves tapes to Import and Export slot.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRTapeMedium -Medium <VBRTapeMedium[]> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet exports selected tapes to the Import and Export slot. You need to to run the exporting procedure if you want to take the tapes out of the tape library.

|  |
| --- |
| ![Export-VBRTapeMedium](images/icon_note.webp) Note: |
| Import and export commands are available only for the devices that support corresponding operations and include I/E slot. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the array of tapes. The cmdlet will export these tapes. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Wait | Defines that the command waits for the import sessions to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupSession](vbrbackupsession.md)

Examples

Exporting Selected Tape

This example shows how to export the 00170008 tape.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "00170008"  Export-VBRTapeMedium -Medium $tape |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Export-VBRTapeMedium cmdlet. Set the $tape variable as the Medium parameter value.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)


