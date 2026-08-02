---
title: "Get-VBRIrisInstanceOriginalPath"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbririsinstanceoriginalpath.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRIrisInstanceOriginalPath


Short Description

Returns original paths of InterSystems IRIS instance data in a restore point.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRIrisInstanceOriginalPath -RestorePoint <Object>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the original paths of InterSystems IRIS instance data stored in a restore point.

Use these paths to create path mapping rules with the [New-VBRIrisInstancePathMappingRule](new-vbririsinstancepathmappingrule.md) cmdlet when you restore an InterSystems IRIS instance to a different location with the [Start-VBRIrisInstanceRestore](start-vbririsinstancerestore.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies the restore point for which you want to get original paths of InterSystems IRIS instance data. | Accepts the Object object. To get this object, run the [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns an array of VBRPath objects that contain the original paths of InterSystems IRIS instance data.

Examples

Getting Original Paths of an InterSystems IRIS Restore Point

This example shows how to get the original paths of InterSystems IRIS instance data stored in a restore point.

|  |
| --- |
| $rp = Get-VBRSnapshotRestorePoint -ObjectName "IRIS01"  Get-VBRIrisInstanceOriginalPath -RestorePoint $rp[0] |

Perform the following steps:

1. Run the [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md) cmdlet. Specify the ObjectName parameter value. Save the result to the $rp variable.
2. Run the Get-VBRIrisInstanceOriginalPath cmdlet. Set the $rp variable as the RestorePoint parameter value.

Related Commands

* [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md)
* [New-VBRIrisInstancePathMappingRule](new-vbririsinstancepathmappingrule.md)
* [Start-VBRIrisInstanceRestore](start-vbririsinstancerestore.md)

Page updated 2026-06-18

