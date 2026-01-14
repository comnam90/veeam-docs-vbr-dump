---
title: "Remove-VBRVMExclusion"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrvmexclusion.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRVMExclusion

In this article

Short Description

Removes global VM exclusions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRVMExclusion -Exclusion <VBRVMExclusion[]>  [<CommonParameters>] |

Detailed Description

This cmdlet removes global exclusions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Exclusion | Specifies global VM exclusions that you want to remove. | Accepts the VBRVMExclusion[] object. To get this object, run the [Get-VBRVMExclusion](get-vbrvmexclusion.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Global VM Exclusion

This example shows how to add a note to the exclusion for the ubuntusrv20 VM.

|  |
| --- |
| $excl = Get-VBRVMExclusion -Name "ubuntusrv20"  Remove-VBRVMExclusion -Exclusion $excl |

Perform the following steps:

1. Run the [Get-VBRVMExclusion](get-vbrvmexclusion.md) cmdlet. Specify the Name parameter value. Save the result to the $excl variable.
2. Run the Set-VBRVMExclusion cmdlet. Set the $excl variable as the Exclusion parameter value.

Related Commands

[Get-VBRVMExclusion](get-vbrvmexclusion.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
