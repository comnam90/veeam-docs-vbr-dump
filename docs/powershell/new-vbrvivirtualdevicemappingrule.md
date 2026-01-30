---
title: "New-VBRViVirtualDeviceMappingRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvivirtualdevicemappingrule.html"
last_updated: "11/5/2024"
product_version: "13.0.1.1071"
---

# New-VBRViVirtualDeviceMappingRule


Short Description

Defines backed-up virtual disk mapping settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRViVirtualDeviceMappingRule -SourceVirtualDevice <VBRViVirtualDevice> [-Datastore <CViDatastoreItem>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines mapping settings of a backed-up virtual disk.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceVirtualDevice | Specifies a backed-up virtual disk. The cmdlet will map this disk to the datastore. | Accepts the VBRViVirtualDevice object. To create this object, run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Datastore | Specifies a datastore. The cmdlet will map backed-up virtual disks to this datastore.  Note: If you do not specify this parameter, the cmdlet will will attach backed-up virtual disks to the default datastore. | Accepts the CViDatastoreItem object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualDeviceMappingRule object that contains backed-up virtual disks mapping settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Mapping Backed-Up Virtual Disks to Default Datastore

|  |  |
| --- | --- |
| This example shows how to map the backed-up virtual disk to the default datastore. The cmdlet will attach the virtual disk of the VM that is backed up by the Winsrv4515 job.  |  | | --- | | $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  New-VBRViVirtualDeviceMappingRule -SourceVirtualDevice $disks[0] |  Perform the following steps:   1. Get the backed-up VM virtual disks:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point will be used.   1. Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Specify the RestorePoint parameter value. Save the result to the $disks variable.   The Get-VBRViVirtualDevice cmdlet will return an array of disks. Consider that the array numbering starts with 0. In our example, the first disk will be used.   1. Run the New-VBRViVirtualDeviceMappingRule cmdlet. Set the $disks[0] variable as the SourceVirtualDevice parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Mapping Backed-Up Virtual Disks to Specific Datastore

|  |  |
| --- | --- |
| This example shows how to map the backed-up virtual disk to the LocalStore\_0 datastore. This datastore is connected to the WinSrv2073 server. The cmdlet will map the virtual disk of the VM that is backed up by the Winsrv4515 job.  |  | | --- | | $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  $server = Get-VBRServer -Name "WinSrv2073"  $datastore = Find-VBRViDatastore -Server $server -Name "LocalStore\_0"  New-VBRViVirtualDeviceMappingRule -SourceVirtualDevice $disks[0] -Datastore $datastore |  Perform the following steps:   1. Get the backed-up VM virtual disks:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point will be used.   1. Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Specify the RestorePoint parameter value. Save the result to the $disks variable.   The Get-VBRViVirtualDevice cmdlet will return an array of disks. Consider that the array numbering starts with 0. In our example, the first disk will be used.   1. Get the datastore:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Name and Server parameter values. Save the result to the $datastore variable.  1. Run the New-VBRViVirtualDeviceMappingRule cmdlet. Set the $disks[0] variable as the SourceVirtualDevice parameter value. Set the $datastore variable as the Datastore parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)


