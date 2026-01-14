---
title: "Enable-VBRTapeProtection"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrtapeprotection.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRTapeProtection

In this article

Short Description

Sets overwrite protection for selected tapes.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRTapeProtection -Medium <VBRTapeMedium[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet sets software overwrite protection for selected tapes.

Protection overrides the retention settings of the media pool to set a lifelong retention period for the selected tapes.

You can set protection for both online or offline tapes that contain data.

The protection can be switched off at any time. The retention settings will be changed to the value set for the media pool. Run the [Disable-VBRTapeProtection](disable-vbrtapeprotection.md) cmdlet to switch off the protection.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the array of tapes. The cmdlet will set protection to these tapes. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMedium[]](vbrtapemedium.md)

Examples

Setting Overwrite Protection to Selected Tape

This example shows how to set protection for the tape named 00140009.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "00140009"  Enable-VBRTapeProtection -Medium $tape -PassThru |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Enable-VBRTapeProtection cmdlet. Set the $tape variable as the Medium parameter value. Provide the PassThru parameter.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
