---
title: "New-VBRGoogleCloudComputeDiskConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrgooglecloudcomputediskconfiguration.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# New-VBRGoogleCloudComputeDiskConfiguration


Short Description

Creates storage volume settings for Google Cloud instances.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRGoogleCloudComputeDiskConfiguration -DiskName <string> -DiskType {BalancedPersistent | SSDPersistent | StandardPersistent}  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRGoogleCloudComputeDiskConfiguration](vbrgooglecloudcomputediskconfiguration.md) object. This object contains disk types of Google Cloud instances. Veeam Backup & Replication will use the specified type when restoring machines to Google Cloud.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DiskName | Specifies the disk of the source machine. Veeam Backup & Replication will restore this disk to Google Cloud.  Note: You must specify the disk name in the "VMNAME.vhdx" format. | String | True | Named | False |
| DiskType | Specifies the storage volume type. Veeam Backup & Replication will save disks of the restored machine as Google Cloud Engine (GCE) disks. You can select the following types of GCE disks:   * BalancedPersistent - use this option to create balanced persistent disks. * SSDPersistent - use this option to create SSD persistent disks. * StandardPersistent - use this option to create standard persistent disks. | Enum | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeDiskConfiguration](vbrgooglecloudcomputediskconfiguration.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Storage Volume Settings for Computer

|  |  |
| --- | --- |
| This example shows how to define standard persistent storage volume for a computer disk backed-up with Veeam Agent for Microsoft Windows.  |  | | --- | | $backup = Get-VBRBackup -Name "Windows Servers Backup"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskNames = Get-VBRComputerDisk -RestorePoint $restorePoint  $diskConfig = New-VBRGoogleCloudComputeDiskConfiguration -DiskName $diskNames[0].UniqueId -DiskType StandardPersistent |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the [Get-VBRComputerDisk](get-vbrcomputerdisk.md) cmdlet. Set the $restorePoint value for the RestorePoint parameter. Save the result to the $diskNames variable. 6. Run the New-VBRGoogleCloudComputeDiskConfiguration cmdlet. Specify the following:  1. Set the $diskNames[0].UniqueId variable as the DiskName parameter value. 2. Specify the DiskType parameter value. 3. Save the result to the $diskConfig variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Storage Volume Settings for Hyper-V VMs

|  |  |
| --- | --- |
| This example shows how to define standard persistent storage volume for a disk of a Microsoft Hyper-V VM.  |  | | --- | | $backup = Get-VBRBackup -Name "VM Backup Job"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskConfig = New-VBRGoogleCloudComputeDiskConfiguration -DiskName $restorePoint.AuxData.Disks[0].TargetFilePath -DiskType StandardPersistent |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the New-VBRAmazonEC2DiskConfiguration cmdlet. Specify the following:  1. Set the $restorePoint.AuxData.Disks[0].TargetFilePath variable as the DiskName parameter value. 2. Specify the DiskType parameter value. 3. Save the result to the $diskConfig variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Storage Volume Settings for Other Workloads

|  |  |
| --- | --- |
| This example shows how to define standard persistent storage volume for for a disk of a workload other than computers backed-up with Veeam Agent for Microsoft Windows. This example shows how to do it for a VMware vSphere VM.  |  | | --- | | $backup = Get-VBRBackup -Name "VM Backup Job"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskConfig = New-VBRGoogleCloudComputeDiskConfiguration -DiskName $restorePoint.AuxData.Disks[0].FileName -DiskType StandardPersistent |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the New-VBRGoogleCloudComputeDiskConfiguration cmdlet. Specify the following:  1. Set the $restorePoint.AuxData.Disks[0].FileName variable as the DiskName parameter value. 2. Specify the DiskType parameter value. 3. Save the result to the $diskConfig variable. |


