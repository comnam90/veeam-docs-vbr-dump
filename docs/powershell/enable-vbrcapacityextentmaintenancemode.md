---
title: "Enable-VBRCapacityExtentMaintenanceMode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcapacityextentmaintenancemode.html"
last_updated: "2/2/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRCapacityExtentMaintenanceMode


Short Description

Enables the Maintenance mode for capacity extents.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRCapacityExtentMaintenanceMode -CapacityExtent <VBRCapacityExtent[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet enables the Maintenance mode for capacity extents of the scale-out backup repository.

Run the [Disable-VBRCapacityExtentMaintenanceMode](disable-vbrcapacityextentmaintenancemode.md) cmdlet to disable the Maintenance mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| CapacityExtent | Specifies the capacity extent. The cmdlet will set this extent to the Maintenance mode. | Accepts the [VBRCapacityExtent](vbrcapacityextent.md)[] object. To get this object, run the [Get-VBRCapacityExtent](get-vbrcapacityextent.md) cmdlet. | True | Named | True (ByValue,  ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Setting Maintenance Mode for Capacity Extent

This example shows how to set the Maintenance mode for the capacity extent.

|  |
| --- |
| $scaleoutrepository = Get-VBRBackupRepository -ScaleOut -Name "Amazon S3"  $extent = Get-VBRCapacityExtent -Repository $scaleoutrepository  Enable-VBRCapacityExtentMaintenanceMode -CapacityExtent $extent |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value and provide ScaleOut parameter. Save the result to the $scaleoutrepository variable.
2. Run the [Get-VBRCapacityExtent](get-vbrcapacityextent.md) cmdlet. Set the $scaleoutrepository variable as Repository parameter value. Save the result to the $extent variable.
3. Run the Enable-VBRCapacityExtentMaintenanceMode cmdlet. Set the $extent variable as the CapacityExtent parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCapacityExtent](get-vbrcapacityextent.md)


