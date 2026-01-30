---
title: "Disable-VBRRepositoryExtentSealedMode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrrepositoryextentsealedmode.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRRepositoryExtentSealedMode


Short Description

Disables Sealed mode for extents of a scale-out backup repository.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRRepositoryExtentSealedMode -Extent <VBRRepositoryExtent[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet disables Sealed mode for extents of a scale-out backup repository.

Run the [Enable-VBRRepositoryExtentSealedMode](enable-vbrrepositoryextentsealedmode.md) cmdlet to enable Sealed mode for extents of a scale-out backup repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Extent | Specifies an array of scale-out repository extents. The cmdlet will disable the Sealed mode for these extents. | Accepts the ID, the String (name of the backup repository that is used as extent), or the [VBRRepositoryExtent](vbrrepositoryextent.md) [] object.  To get the performance extent, run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet.  To get the capacity extent, run the [Get-VBRCapacityExtent](get-vbrcapacityextent.md) cmdlet.  To get the archive extent, run the [Get-VBRArchiveExtent](get-vbrarchiveextent.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Sealed Mode for Capacity Extents

This example shows how to disable Sealed mode for capacity extents of a scale-out backup repository.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  $extent = Get-VBRCapacityExtent -Repository $repository  Disable-VBRRepositoryExtentSealedMode -Extent $extent |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter value. Save the result to the $repository variable.
2. Run the [Get-VBRCapacityExtent](get-vbrcapacityextent.md) cmdlet. Set the $repository variable as the Repository parameter value. Save the result to the $extent variable.
3. Run the Disable-VBRRepositoryExtentSealedMode cmdlet. Set the $extent variable as the Extent parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCapacityExtent](get-vbrcapacityextent.md)


