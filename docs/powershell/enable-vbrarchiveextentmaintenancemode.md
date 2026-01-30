---
title: "Enable-VBRArchiveExtentMaintenanceMode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrarchiveextentmaintenancemode.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRArchiveExtentMaintenanceMode


Short Description

Enables the Maintenance mode for the archive extent.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRArchiveExtentMaintenanceMode -ArchiveExtent <VBRArchiveExtent[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet enables the Maintenance mode for the archive extent of the scale-out backup repository.

Run the [Disable-VBRArchiveExtentMaintenanceMode](disable-vbrarchiveextentmaintenancemode.md) cmdlet to disable the Maintenance mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ArchiveExtent | Specifies the archive extent. The cmdlet will set this extent to the Maintenance mode. | Accepts the [VBRArchiveExtent](vbrarchiveextent.md) object. To get this object, run the [Get-VBRArchiveExtent](get-vbrarchiveextent.md) cmdlet. | True | Named | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Enabling Maintenance Mode for Archive Extent

This example shows how to set the Maintenance mode for the archive extent.

|  |
| --- |
| $scaleoutrepository = Get-VBRBackupRepository -ScaleOut -Name "Amazon S3"  $extent = Get-VBRArchiveExtent -Repository $scaleoutrepository  Enable-VBRArchiveExtentMaintenanceMode -ArchiveExtent $extent |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Specify the Name parameter value. Save the result to the $scaleoutrepository variable.
2. Run the [Get-VBRArchiveExtent](get-vbrarchiveextent.md) cmdlet. Set the $scaleoutrepository variable as the Repository parameter value. Save the result to the $extent variable.
3. Run the Enable-VBRArchiveExtentMaintenanceMode cmdlet. Set the $extent variable as the ArchiveExtent parameter value.

Related Commands

* [Get-VBRArchiveExtent](get-vbrarchiveextent.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


