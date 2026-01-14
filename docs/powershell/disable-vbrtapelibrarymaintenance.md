---
title: "Disable-VBRTapeLibraryMaintenance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrtapelibrarymaintenance.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRTapeLibraryMaintenance

In this article

Short Description

Disables the Maintenance mode for a tape library or a standalone tape drive.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRTapeLibraryMaintenance -Library <VBRTapeLibrary[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

The cmdlet disables the Maintenance mode for a tape library or a standalone tape drive.

Run the [Enable-VBRTapeLibraryMaintenance](enable-vbrtapelibrarymaintenance.md) cmdlet to enable the Maintenance mode for a tape library or a standalone tape drive.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Library | Specifies an array of tape libraries. The cmdlet will disable the Maintenance mode for this array of tape libraries. | Accepts the [VBRTapeLibrary[]](vbrtapelibrary.md) object. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Maintenance Mode for Tape Library

This example shows how to disable the Maintenance mode for the HP MSL G3 Series 5.30 tape library.

|  |
| --- |
| $library = Get-VBRTapeLibrary -Name "HP MSL G3 Series 5.30"  Disable-VBRTapeLibraryMaintenance -Library $library |

Perform the following steps:

1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save the result to the $library variable.
2. Run the Disable-VBRTapeLibraryMaintenance cmdlet. Set the $library variable as the Library parameter value.

Related Commands

[Get-VBRTapeLibrary](get-vbrtapelibrary.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
