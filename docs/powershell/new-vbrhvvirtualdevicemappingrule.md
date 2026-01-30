---
title: "New-VBRHvVirtualDeviceMappingRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvvirtualdevicemappingrule.html"
last_updated: "11/29/2024"
product_version: "13.0.1.1071"
---

# New-VBRHvVirtualDeviceMappingRule


Short Description

Defines mapping settings of a backed-up virtual disk.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvVirtualDeviceMappingRule -Path <String> -SourceDevice <VBRViVirtualDevice>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRHvVirtualDeviceMappingRule object that contains mapping settings of a VMware backed-up virtual disk to Hyper-V target host file path.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceDevice | Specifies a backed-up virtual disk. The cmdlet will map this disk to the Hyper-V file path. | Accepts the VBRViVirtualDevice object. To create this object, run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Path | Specifies a path on Hyper-V host for a backed-up virtual disk. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvVirtualDeviceMappingRule object that contains backed-up virtual disk mapping settings.

Examples

Mapping Backed-Up Virtual Disks to Hyper-V Host File Path

This example shows how to map the backed-up virtual disk to the custom filepath on the Hyper-V host. The cmdlet will map the virtual disk of the VM that is backed up by the Winsrv4515 job.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  New-VBRHvVirtualDeviceMappingRule -SourceDevice $disks[0] -Path "D:\VMs\disks" |

Perform the following steps:

1. Get the backed-up VM virtual disks:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point will be used.

1. Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Set the $restorepoint[3] as the RestorePoint parameter value. Save the result to the $disks variable.

The Get-VBRViVirtualDevice cmdlet will return an array of disks. Consider that the array numbering starts with 0. In our example, the first disk will be used.

1. Run the New-VBRHvVirtualDeviceMappingRule cmdlet. Set the $disks[0] variable as the SourceVirtualDevice parameter value. Specify the Path parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md)


