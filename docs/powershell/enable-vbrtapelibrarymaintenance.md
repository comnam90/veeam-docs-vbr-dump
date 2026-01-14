---
title: "Enable-VBRTapeLibraryMaintenance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrtapelibrarymaintenance.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRTapeLibraryMaintenance

In this article

Short Description

Enables the Maintenance mode for a tape library or a standalone tape drive.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRTapeLibraryMaintenance -Library <VBRTapeLibrary[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

The cmdlet enables the Maintenance mode for a tape library or a standalone tape drive.

You can run this cmdlet to lock a tape library or a standalone tape drive so that Veeam Backup & Replication will not be able to use them for tape jobs. This action might be necessary in case you want to provide maintenance services to them.

Run the [Disable-VBRTapeLibraryMaintenance](disable-vbrtapelibrarymaintenance.md) cmdlet to disable the Maintenance mode.

|  |
| --- |
| Note |
| Before you enable the Maintenance mode for the tape library, consider the following:   * You cannot enable the Maintenance mode for the tape library if the jobs that use this tape library are in the running state. * After you enable the Maintenance mode for the tape library, all jobs that use it will fail with an error when starting. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Library | Specifies an array of tape libraries. The cmdlet will enable the Maintenance mode for this array of tape libraries. | Accepts the [VBRTapeLibrary[]](vbrtapelibrary.md) object. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Maintenance Mode for Tape Library

This example shows how to enable the Maintenance mode for the HP MSL G3 Series 5.30 tape library.

|  |
| --- |
| $library = Get-VBRTapeLibrary -Name "HP MSL G3 Series 5.30"  Enable-VBRTapeLibraryMaintenance -Library $library |

Perform the following steps:

1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save the result to the $library variable.
2. Run the Enable-VBRTapeLibraryMaintenance cmdlet. Set the $library variable as the Library parameter value.

Related Commands

[Get-VBRTapeLibrary](get-vbrtapelibrary.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
