---
title: "Get-VBRTapeCopyDependentMedium"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapecopydependentmedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeCopyDependentMedium

In this article

Short Description

Returns dependent tapes.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRTapeCopyDependentMedium -Medium <VBRTapeMedium[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns dependent tapes that store other parts of the backup.

When a backup file does not fit on one tape, it is divided into parts and written to several tapes. These tapes are considered dependent. You may want to run this cmdlet before you start the [Start-VBRTapeCopy](start-vbrtapecopy.md) cmdlet, to get information on the dependent tapes.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies an array of tapes. The cmdlet will return dependent tapes for the tapes from this array. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To create this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRTapeCopyDependentMedium object that defines dependent tapes that store dependent parts of the backup files.

Examples

Getting Dependent Tapes for Specified Tape

This example shows how to get tapes that are dependent on the 0021000C tape.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "0021000C"  Get-VBRTapeCopyDependentMedium -Medium $tape |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Get-VBRTapeCopyDependentMedium cmdlet. Set the $tape variable as the Medium parameter value.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
