---
title: "Add-VBRvCloudBackupCopyJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcloudbackupcopyjob.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Add-VBRvCloudBackupCopyJob (obsolete)

In this article

Short Description

Creates a Cloud Director backup copy job.

|  |
| --- |
| Important |
| This cmdlet is obsolete and only works for creating a simple mode backup copy job. It is recommended to create a new backup job using the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCloudBackupCopyJob -SourceAccelerator <CWanAccelerator> -TargetAccelerator <CWanAccelerator> [-Name <String>] [-Description <String>] [-Entity <IVcdItem[]>] [-Backup <CBackup[]>] [-BackupJob <CBackupJob[]>] [-SourceRepository <CBackupRepository[]>] [-Repository <CBackupRepository>] [-Force] [-EnableImmediateCopy]  [<CommonParameters>]  -OR-  Add-VBRvCloudBackupCopyJob -DirectOperation <SwitchParameter> [-Name <String>] [-Description <String>] [-Entity <IVcdItem[]>] [-Backup <CBackup[]>] [-BackupJob <CBackupJob[]>] [-SourceRepository <CBackupRepository[]>] [-Repository <CBackupRepository>] [-Force] [-EnableImmediateCopy]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Cloud Director backup copy job. The Cloud Director backup copy job uses a cloud repository as the target.

To add the VMs for the backup copy job, you can add VMs, backups or backup jobs. Veeam will use this data to copy the backups of the needed VM.

You can transfer data in the following ways:

* Using WAN accelerators. This mode is recommended for off-site backups.

To create and run a backup copy job using WAN accelerators you need to have source and target WAN accelerators created. Run the [Add-VBRWANAccelerator](add-vbrwanaccelerator.md) cmdlet to create a WAN accelerator. WAN optimization is available only in Veeam Backup & Replication Enterprise Plus, Veeam Universal License Edition.

* Directly. With this method, the job sends the data directly to the target backup repository without performing data deduplication. This mode is recommended for on-site backups, or off-site backups using fast connections.

Use an appropriate parameter set for each way.

Note that the backup copy job is created in disabled state. Run the [Enable-VBRJob](enable-vbrjob.md) cmdlet to start the job running on the defined schedule.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the backup copy job. | String | False | Named | False |
| Entity | Specifies the array of VMs you want to add to the job. | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Backup | Specifies the array of backups. The cmdlet will add VMs from these backups to the Cloud Director backup copy job. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | False |
| BackupJob | Specifies the array of backup jobs. The cmdlet will add VMs from these backup jobs to the Cloud Director backup copy job. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |
| SourceRepository | Specifies an array of source backup repositories. | Accepts the CBackupRepository[] object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md)cmdlet. | False | Named | False |
| Repository | Specifies the target backup repository to where you want to copy the VM data.  Default: default backup repository. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md)cmdlet. | False | Named | False |
| SourceAccelerator | Specifies the WAN accelerator on the source side.  If you select the mode using WAN accelerators, the -DirectOperation parameter should be omitted. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| TargetAccelerator | Specifies the WAN accelerator on the target side.  If you select the mode using WAN accelerators, the -DirectOperation parameter should be omitted. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the backup copy job. | String | False | Named | False |
| DirectOperation | Enables the direst operation method sending the data directly to the target backup repository without performing data deduplication.  If you select the direct operation mode, the -TargetAccelerator and -SourceAccelerator parameters should be omitted. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will create a new Cloud Director backup copy job without showing warnings in the PowerShell console. | SwitchParameter | SwitchParameter | False | Named |
| EnableImmediateCopy | Defines that the cmdlet will enable the immediate copy mode.  If you specify this parameter, Veeam Backup & Replication will copy new restore points and logs as soon as they appear.  Otherwise, Veeam Backup & Replication will copy data from backups once per backup copy interval. | SwitchParameter | SwitchParameter | False | Named |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Cloud Backup Copy Job with WAN Accelerators

|  |  |
| --- | --- |
| This example shows how to create the CopyJob1 Cloud backup copy job processed through WAN accelerators.  |  | | --- | | $wansource = Get-VBRWANAccelerator -Name "Sydney WAN"  $wantarget = Get-VBRWANAccelerator -Name "London WAN"  $vms = Find-VBRvCloudEntity -Name "srv2024" -Vm  $repository = Get-VBRBackupRepository -Name "Backups Vol2"  Add-VBRvCloudBackupCopyJob -SourceAccelerator $wansource -TargetAccelerator $wantarget -Name "CopyJob1" -Entity $vms -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $wansource variable. 2. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $wantarget variable. 3. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name parameter value. Provide the Vm parameter. Save the result to the $vms variable. 4. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 5. Run the Add-VBRvCloudBackupCopyJob cmdlet. Specify the following settings:  * Set the $wansource variable as the SourceAccelerator parameter value. * Set the $wantarget variable as the TargetAccelerator parameter value. * Specify the Name parameter value. * Set the $vms variable as the Entity parameter value. * Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Cloud Backup Copy Job with Direct Data Transfer

|  |  |
| --- | --- |
| This example shows how to create the DC CopyJob Cloud backup copy job with the direct data transfer.  |  | | --- | | Get-VBRBackup -Name "DC Backup" | Add-VBRvCloudBackupCopyJob -DirectOperation -Name "DC CopyJob" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VBRvCloudBackupCopyJob cmdlet. Provide the DirectOperation parameter. Specify the Name parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
