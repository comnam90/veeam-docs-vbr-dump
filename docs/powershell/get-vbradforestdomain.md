---
title: "Get-VBRADForestDomain"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbradforestdomain.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRADForestDomain


Short Description

Returns Active Directory domains within a forest or a restore point.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Microsoft Active Directory forest domains using the Microsoft Active Directory forest.

|  |
| --- |
| Get-VBRADForestDomain -ADForest <VBRADForest> [<CommonParameters>] |

* Get Microsoft Active Directory forest domains using a restore point.

|  |
| --- |
| Get-VBRADForestDomain -RestorePoint <VBRADForestRestorePoint> [<CommonParameters>] |

Detailed Description

The cmdlet returns all Active Directory domains in the specified Microsoft Active Directory forest or restore point, including domains from every domain tree in the forest.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| ADForest | Specifies a Microsoft Active Directory forest object. The cmdlet will return Active Directory domains within that forest. | Accepts the [VBRADForest](vbradforest.md) object. To get this object, run the [Get-VBRADForest](get-vbradforest.md) cmdlet. | True | Named | True (ByValue) |
| RestorePoint | Specifies a Microsoft Active Directory forest restore point. The cmdlet will return Active Directory domains within that restore point. | Accepts the [VBRADForestRestorePoint](vbradforestrestorepoint.md) object. To get this object, run the [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestDomain](vbradforestdomain.md)[] object that contains information about the Active Directory domain.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Domains from Microsoft Active Directory Forest

|  |  |
| --- | --- |
| This example shows how to get Active Directory domains by specifying the forest.  |  | | --- | | $forest = Get-VBRADForest  Get-VBRADForestDomain -ADForest $forest |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the Get-VBRADForestDomain cmdlet. Set the $forest variable as the ADForest parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Domains from Forest Restore Point

|  |  |
| --- | --- |
| This example shows how to get Active Directory domains by specifying a forest restore point.  |  | | --- | | $forest = Get-VBRADForest  $restorePoint = Get-VBRADForestRestorePoint -ADForest $forest  Get-VBRADForestDomain -RestorePoint $restorePoint |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $restorePoint variable. 3. Run the Get-VBRADForestDomain cmdlet. Set the $restorePoint variable as the RestorePoint parameter value. |

Related Commands

* [Get-VBRADForest](get-vbradforest.md)
* [Get-VBRADForestRestorePoint](get-vbradforestrestorepoint.md)

Page updated 2026-07-28

