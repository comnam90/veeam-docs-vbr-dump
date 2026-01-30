---
title: "New-VBRAmazonEC2DiskConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbramazonec2diskconfiguration.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# New-VBRAmazonEC2DiskConfiguration


Short Description

Creates storage volume settings for Amazon EC2 instances.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAmazonEC2DiskConfiguration -DiskName <string> [-Include] [-DiskType <VBRAmazonEC2DiskType>{GeneralPurposeSSD | ProvisionedIOPSSSD | ColdHDD | ThroughtputOptimizedHDD | Magnetic}] [-ProvisionedIOPSNumber <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRAmazonEC2DiskConfiguration object. This object contains storage volume settings for Amazon EC2 instances.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DiskName | Specifies the disk of the source machine. Veeam Backup & Replication will restore this disk to Amazon EC2.  Note: You must specify the disk name in the "VMNAME.vhdx" format. | String | True | Named | False |
| Include | Defines that Veeam Backup & Replication will restore selected disks to Amazon EC2.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| DiskType | Specifies the storage volume type. Veeam Backup & Replication will saves disks of the restored machine as Amazon Elastic Block Store (EBS) volumes. You can select the following types of EBS volumes:   * GeneralPurposeSSD - use this option to create General Purpose SSD (gp2) volumes. * ProvisionedIOPSSSD - use this option to create Provisioned IOPS SSD volumes. * ColdHDD - use this option to create Cold HDD volumes. * ThroughtputOptimizedHDD - use this option to create Throughput Optimized HDD volumes. * Magnetic - use this option to create Magnetic volumes. * GeneralPurposeSSD3 - use this option to create General Purpose SSD (gp3) volumes. * ProvisionedIOPSSSD2 - use this option to create Provisioned IOPS SSD (io2) volumes. | VBRAmazonEC2DiskType | False | Named | False |
| ProvisionedIOPSNumber | For the ProvisionedIOPSSSD option.  Specifies the number of input/output operations per second for the volume. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Storage Volume Settings for Computer

|  |  |
| --- | --- |
| This example shows how to define Cold HDD storage volume for a computer disk backed-up with Veeam Agent for Microsoft Windows.  |  | | --- | | $backup = Get-VBRBackup -Name "Windows Servers Backup"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskNames = Get-VBRComputerDisk -RestorePoint $restorePoint  $diskConfig = New-VBRAmazonEC2DiskConfiguration -DiskName $diskNames[0].UniqueId -DiskType ColdHDD -Include |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the [Get-VBRComputerDisk](get-vbrcomputerdisk.md) cmdlet. Set the $restorePoint value for the RestorePoint parameter. Save the result to the $diskNames variable. 6. Run the New-VBRAmazonEC2DiskConfiguration cmdlet. Specify the following:  1. Set the $diskNames[0].UniqueId variable as the DiskName parameter value. 2. Specify the DiskType and Include parameter values. 3. Save the result to the $diskConfig variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Storage Volume Settings for Hyper-V VMs

|  |  |
| --- | --- |
| This example shows how to define Cold HDD storage volume for a disk of a Microsoft Hyper-V VM.  |  | | --- | | $backup = Get-VBRBackup -Name "VM Backup Job"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskConfig = New-VBRAmazonEC2DiskConfiguration -DiskName $restorePoint.AuxData.Disks[0].TargetFilePath -DiskType ColdHDD -Include |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the New-VBRAmazonEC2DiskConfiguration cmdlet. Specify the following:  1. Set the $restorePoint.AuxData.Disks[0].TargetFilePath variable as the DiskName parameter value. 2. Specify the DiskType and Include parameter values. 3. Save the result to the $diskConfig variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Storage Volume Settings for Other Workloads

|  |  |
| --- | --- |
| This example shows how to define Cold HDD storage volume for for a disk of a workload other than computers backed-up with Veeam Agent for Microsoft Windows. This example shows how to do it for a VMware vSphere VM.  |  | | --- | | $backup = Get-VBRBackup -Name "VM Backup Job"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskConfig = New-VBRAmazonEC2DiskConfiguration -DiskName $restorePoint.AuxData.Disks[0].FileName -DiskType ColdHDD -Include |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the New-VBRAmazonEC2DiskConfiguration cmdlet. Specify the following:  1. Set the $restorePoint.AuxData.Disks[0].FileName variable as the DiskName parameter value. 2. Specify the DiskType and Include parameter values. 3. Save the result to the $diskConfig variable. |


