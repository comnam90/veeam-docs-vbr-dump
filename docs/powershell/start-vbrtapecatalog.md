---
title: "Start-VBRTapeCatalog"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtapecatalog.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Start-VBRTapeCatalog

In this article

Short Description

Starts tape catalog process.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start tape catalog process for selected libraries.

|  |
| --- |
| Start-VBRTapeCatalog -Library <VBRTapeLibrary[]> [-Wait]  [<CommonParameters>] |

* Start catalog process for selected tapes.

|  |
| --- |
| Start-VBRTapeCatalog -Medium <VBRTapeMedium[]> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts catalog process. Catalog process scans tape contents and registers tapes in the Veeam Backup & Replication database after which Veeam Backup & Replication is able to administrate tape allocation and consumption and track data written to tapes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Library | Specifies the array of tape libraries. The cmdlet will catalog these tape libraries. | Accepts the [VBRTapeLibrary[]](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Medium | Specifies the array of tapes. The cmdlet will catalog these tapes. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupSession](vbrbackupsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Cataloging Selected Library [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to catalog a selected library.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Start-VBRTapeCatalog |  Perform the following steps:   1. Run the Get-VBRTapeLibrary cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Start-VBRTapeCatalog cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Cataloging Selected Tapes [Using Variable]

|  |  |
| --- | --- |
| This example shows how to catalog selected tapes.  |  | | --- | | $tape = Get-VBRTapeMedium -Name "00140009","00140010"  Start-VBRTapeCatalog -Medium $tape |  Perform the following steps:   1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable. 2. Run the Start-VBRTapeCatalog cmdlet. Set the $tape variable as the Medium parameter value. |

Related Commands

* [Get-VBRTapeLibrary](get-vbrtapelibrary.md)
* [Get-VBRTapeMedium](get-vbrtapemedium.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
