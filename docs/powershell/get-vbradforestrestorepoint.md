---
title: "Get-VBRADForestRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbradforestrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRADForestRestorePoint


Short Description

Returns restore points for a Microsoft Active Directory forest.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRADForestRestorePoint -ADForest <VBRADForest> [<CommonParameters>] |

Detailed Description

The cmdlet returns restore points that are available for the specified Microsoft Active Directory forest.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| ADForest | Specifies the Microsoft Active Directory forest for which to return restore points. | Accepts the [VBRADForest](vbradforest.md) object. To get this object, run the [Get-VBRADForest](get-vbradforest.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestRestorePoint](vbradforestrestorepoint.md)[] array that contains restore points for the specified Microsoft Active Directory forest.

Examples

Getting Restore Points for Microsoft Active Directory Forest

This example shows how to get all restore points available for a Microsoft Active Directory forest.

|  |
| --- |
| $forest = Get-VBRADForest  Get-VBRADForestRestorePoint -ADForest $forest |

Perform the following steps:

1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable.
2. Run the Get-VBRADForestRestorePoint cmdlet. Set the $forest variable as the ADForest parameter value.

Related Commands

* [Get-VBRADForest](get-vbradforest.md)
* [Get-VBRADForestDomain](get-vbradforestdomain.md)

Page updated 2026-07-28

