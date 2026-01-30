---
title: "Enable-VBRRepositoryExtentMaintenanceMode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrrepositoryextentmaintenancemode.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRRepositoryExtentMaintenanceMode


Short Description

Enables Maintenance mode for a performance extent or capacity extent of a scale-out backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRRepositoryExtentMaintenanceMode -Extent <VBRRepositoryExtent[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet enables Maintenance mode for a selected performance extent or extents of scale-out backup repositories.

With one command, you can switch to Maintenance mode multiple performance extents: the extents can be of mixed policies and belong to several scale-out repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Extent | Specifies the array of scale-out repository extents. The cmdlet will enable the Maintenance mode for these extents.  Accepts extents with different policies and of different scale-out repositories. | Accepts the ID, the String (name of the backup repository that is used as extent), or the [VBRRepositoryExtent](vbrrepositoryextent.md) [] object.  To get the performance extent, run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet.  To get the capacity extent, run the [Get-VBRCapacityExtent](get-vbrcapacityextent.md) cmdlet.  To get the archive extent, run the [Get-VBRArchiveExtent](get-vbrarchiveextent.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Enabling Maintenance Mode for Performance Extents

This example shows how to enable the Maintenance mode for the performance extents.

|  |
| --- |
| $scaleoutrepository = Get-VBRBackupRepository -ScaleOut -Name "Amazon S3"  $extent = Get-VBRRepositoryExtent -Repository $scaleoutrepository  Enable-VBRRepositoryExtentMaintenanceMode -Extent $extent[2] |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value and provide the ScaleOut parameter. Save the result to the $scaleoutrepository variable.
2. Run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet. Set the $scaleoutrepository variable as the Repository parameter value.Save the result to the $extent variable.

The [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet will return an array of extents. Mind the ordinal number of the necessary extent (in our example, it is the third extent in the array).

1. Run the Enable-VBRRepositoryExtentMaintenanceMode cmdlet. Set the $extent variable as the Extent parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md)


