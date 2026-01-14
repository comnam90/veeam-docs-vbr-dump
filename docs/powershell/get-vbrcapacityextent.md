---
title: "Get-VBRCapacityExtent"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcapacityextent.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCapacityExtent

In this article

Short Description

Returns the capacity extents.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCapacityExtent -Repository <VBRScaleOutBackupRepository[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the capacity extent of scale-out backup repositories. The capacity extent is an object storage repository that is added to the scale-out backup repository and constitutes a capacity tier.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an array of scale-out backup repositories. The cmdlet will return the capacity extent added to this repository. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md)[] object. To get the object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCapacityExtent[]](vbrcapacityextent.md)

Examples

Getting Capacity Extents Added to Scale-Out Backup Repository

This example shows how to get the capacity extents added to the scale-out backup repository.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  Get-VBRCapacityExtent -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Save the result to the $repository variable.
2. Run the Get-VBRCapacityExtent cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
