---
title: "Set-VBRVMExclusion"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvmexclusion.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRVMExclusion

In this article

Short Description

Modifies a global VM exclusion.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRVMExclusion -Exclusion <VBRVMExclusion> [-Note <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a global VM exclusion.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Exclusion | Specifies the global exclusion that you want to modify. | Accepts the VBRVMExclusion object. To get this object, run the [Get-VBRVMExclusion](get-vbrvmexclusion.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| Note | Specifies the note for the exclusion. | String | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVMExclusion object that defines the modified exclusion.

Examples

Adding Notes to Exclusion

This example shows how to add a note to the exclusion for the ubuntusrv20 VM.

|  |
| --- |
| $excl = Get-VBRVMExclusion -Name "ubuntusrv20"  Set-VBRVMExclusion -Exclusion $excl -Note "Protected by another backup server" |

Perform the following steps:

1. Run the [Get-VBRVMExclusion](get-vbrvmexclusion.md) cmdlet. Specify the Name parameter value. Save the result to the $excl variable.
2. Run the Set-VBRVMExclusion cmdlet. Set the $excl variable as the Exclusion parameter value. Specify the Note parameter value.

Related Commands

[Get-VBRVMExclusion](get-vbrvmexclusion.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
