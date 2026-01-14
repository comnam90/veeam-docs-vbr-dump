---
title: "Get-VBRRepositoryExtent"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrepositoryextent.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRRepositoryExtent

In this article

Short Description

Returns scale-out performance extents.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRRepositoryExtent -Repository <VBRScaleOutBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet returns performance extents of scale-out backup repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the scale-out backup repository. The cmdlet will return performance extents added to this repository. | Accepts the GUID, or the String (repository name), or the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRRepositoryExtent[]](vbrrepositoryextent.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Performance Extents of Scale-Out Backup Repository

|  |  |
| --- | --- |
| This command returns performance extents of the Veeam Performance Scale-Out Repository. The scale-out repository is specified by name.  |  | | --- | | Get-VBRRepositoryExtent -Repository "Veeam Performance Scale-Out Repository" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Performance Extents of Scale-Out Backup Repository [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to return performance extents of the Veeam Performance Scale-Out Repository.  |  | | --- | | Get-VBRBackupRepository -Name "Veeam Performance Scale-Out Repository" -ScaleOut | Get-VBRRepositoryExtent |  Perform the following steps:   1. Run the Get-VBRBackupRepository cmdlet. Specify the Name parameter value and provide the ScaleOut parameter. 2. Pipe the cmdlet output to the Get-VBRRepositoryExtent cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Performance Extents of Scale-Out Backup Repository [Using Variable]

|  |  |
| --- | --- |
| This example shows how to return performance extents of the Veeam Performance Scale-Out Repository.  |  | | --- | | $scaleoutrepository = Get-VBRBackupRepository -Name "Veeam Performance Scale-Out Repository" -ScaleOut  Get-VBRRepositoryExtent -Repository $scaleoutrepository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value and provide the ScaleOut parameter. Save the result to the $scaleoutrepository variable. 2. Run the Get-VBRRepositoryExtent cmdlet. Set the $scaleoutrepository variable as the Repository parameter value. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 4/19/2024

Page content applies to build 13.0.1.1071
