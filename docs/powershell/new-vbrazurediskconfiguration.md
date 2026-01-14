---
title: "New-VBRAzureDiskConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazurediskconfiguration.html"
last_updated: "10/15/2025"
product_version: "13.0.1.1071"
---

# New-VBRAzureDiskConfiguration

In this article

Short Description

Defines Azure VM disk types.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define Azure VM disk type using the disk name.

|  |
| --- |
| New-VBRAzureDiskConfiguration -DiskName <String> -DiskType <VBRAzureDiskType> [-Include]  [<CommonParameters>] |

* Define Azure VM disk type using the disk ID.

|  |
| --- |
| New-VBRAzureDiskConfiguration -DiskUid <String> -DiskType <VBRAzureDiskType> [-Include]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRAzureDiskConfiguration object that defines Azure VM disk types. Veeam Backup & Replication will attach disks of these types to the restored workloads.

For more information on disk types, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-machines/disks-types#standard-hdds).

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DiskName | Specifies the name of a disk whose type you want to change during further restore.  Note: The disk must exist in the backup from which you plan to restore. | String | True | Named | False |
| DiskUid | Specifies the ID of a disk whose type you want to change during further restore.  Note: The disk must exist in the backup from which you plan to restore. | String | True | Named | False |
| DiskType | Specifies the type of the disk that Veeam Backup & Replication will attach to the restored workloads. You can specify the following type:   * StandardHDD * StandardSSD * PremiumSSD | VBRAzureDiskType | False | Named | False |
| Include | Defines that the cmdlet will attach an Azure VM disk to the restored workloads. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureDiskConfiguration](vbrazurediskconfiguration.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Azure VM Disk Type for Computer

|  |  |
| --- | --- |
| This example shows how to define the Azure StandardHDD disk type for a computer disk backed-up with Veeam Agent for Microsoft Windows.  |  | | --- | | $backup = Get-VBRBackup -Name "Windows Servers Backup"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskNames = Get-VBRComputerDisk -RestorePoint $restorePoint  $diskConfig = New-VBRAzureDiskConfiguration -DiskName $diskNames[0].UniqueId -DiskType StandardHDD -Include |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the [Get-VBRComputerDisk](get-vbrcomputerdisk.md) cmdlet. Set the $restorePoint value for the RestorePoint parameter. Save the result to the $diskNames variable. 6. Run the New-VBRAzureDiskConfiguration cmdlet. Specify the following:  1. Set the $diskNames[0].UniqueId variable as the DiskName parameter value. 2. Specify the DiskType and Include parameter values. 3. Save the result to the $diskConfig variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Azure VM Disk Type for Hyper-V VMs

|  |  |
| --- | --- |
| This example shows how to define the Azure StandardHDD disk type for disks of Microsoft Hyper-V VMs.  |  | | --- | | $backup = Get-VBRBackup -Name "VM Backup Job"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskConfig = New-VBRAzureDiskConfiguration -DiskName $restorePoint.AuxData.Disks[0].TargetFilePath -DiskType StandardHDD -Include |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the New-VBRAzureDiskConfiguration cmdlet. Specify the following:  1. Set the $restorePoint.AuxData.Disks[0].TargetFilePath variable as the DiskName parameter value. 2. Specify the DiskType and Include parameter values. 3. Save the result to the $diskConfig variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Azure VM Disk Type for Other Workloads

|  |  |
| --- | --- |
| This example shows how to define the Azure StandardHDD disk type for disks of workloads other than computers backed-up with Veeam Agent for Microsoft Windows. This example shows how to do it for a VMware vSphere VM.  |  | | --- | | $backup = Get-VBRBackup -Name "VM Backup Job"  $restorePoint = Get-VBRRestorePoint -Backup $backup | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $diskConfig = New-VBRAzureDiskConfiguration -DiskName $restorePoint.AuxData.Disks[0].FileName -DiskType StandardHDD -Include |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. Save the result to the $restorePoint variable. 5. Run the New-VBRAzureDiskConfiguration cmdlet. Specify the following:  1. Set the $restorePoint.AuxData.Disks[0].FileName variable as the DiskName parameter value. 2. Specify the DiskType and Include parameter values. 3. Save the result to the $diskConfig variable. |

Page updated 10/15/2025

Page content applies to build 13.0.1.1071
