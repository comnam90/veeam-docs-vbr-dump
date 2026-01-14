---
title: "Add-VBRHvBackupCopyJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvbackupcopyjob.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Add-VBRHvBackupCopyJob (obsolete)

In this article

Short Description

Creates a Hyper-V backup copy job.

|  |
| --- |
| Note |
| This cmdlet is obsolete and only works for creating a simple mode backup copy job. It is recommended to create a new backup job using the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |

Applies to

Platform: Hyper-V

For VMware, run the [Add-VBRViBackupCopyJob](add-vbrvibackupcopyjob.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides two parameter sets.

* For data transfer with WAN accelerators:

|  |
| --- |
| Add-VBRHvBackupCopyJob -SourceAccelerator <CWanAccelerator> -TargetAccelerator <CWanAccelerator> [-Name <string>] [-Description <string>] [-Entity <IHvItem[]>] [-Backup <CBackup[]>] [-BackupJob <CBackupJob[]>] [-Repository <CBackupRepository>] [-Force] [-EnableImmediateCopy]  [<CommonParameters>] |

* For direct data transfer:

|  |
| --- |
| Add-VBRHvBackupCopyJob -DirectOperation [-Name <string>] [-Description <string>] [-Entity <IHvItem[]>] [-Backup <CBackup[]>] [-BackupJob <CBackupJob[]>] [-Repository <CBackupRepository>] [-Force] [-EnableImmediateCopy]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Hyper-V backup copy job.

You can use VMs, backups or backup jobs as a source for the backup copy job. Veeam will use this data to copy the backups of the needed VMs.

You can transfer data in the following ways:

* Using WAN accelerators. This mode is recommended for off-site backups.

To create and run a backup copy job using WAN accelerators you need to have source and target WAN accelerators created. Run the [Add-VBRWANAccelerator](add-vbrwanaccelerator.md) cmdlet to create a WAN accelerator. WAN optimization is available only in Veeam Backup & Replication Enterprise Plus, Veeam Universal License Edition.

* Directly. With this method, the job sends the data directly to the target backup repository without performing data deduplication. This mode is recommended for on-site backups, or off-site backups using fast connections.

Use an appropriate parameter set for each way.

Note that the backup copy job is created in disabled state. Run the [Enable-VBRJob](enable-vbrjob.md) cmdlet to start the job running on the defined schedule.

|  |
| --- |
| ![Add-VBRHvBackupCopyJob (obsolete)](images/icon_note.webp) Note: |
| The cmdlet will not run if the geographic location of the VMs added to the job and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| SourceAccelerator | Specifies the WAN accelerator on the source side.  Note that this parameter is required if the Direct Operation is not used (the DirectOperation parameter is not specified). If you specify this parameter and the repository specified in the Repository parameter is not cloud, you must also specify the TargetAccelerator parameter. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| TargetAccelerator | Specifies the WAN accelerator on the target side.  Note that this parameter is required if the WAN acceleration is used (the SourceAccelerator is specified) and the repository specified in the Repository parameter is not cloud. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| DirectOperation | Enables direct operation method sending the data directly to the target backup repository without performing data deduplication.  Note that this parameter is required if the WAN acceleration is not used (the SourceAccelerator and TargetAccelerator parameters are not specified). | SwitchParameter | True | Named | False |
| Name | Specifies the name you want to assign to the backup copy job. | String | False | Named | False |
| Entity | Specifies the array of VMs you want to add to the backup copy job.  Note: You can create a job without source and link it to a backup job after. | Accepts the IHvItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Backup | Specifies the array of backups. The cmdlet will add VMs from these backups to the backup copy job. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | False |
| BackupJob | Specifies the array of backup jobs. The cmdlet will add VMs processed by these jobs to the backup copy job. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |
| Repository | Specifies the backup repository to where you want to copy the VM data.  Default: default backup repository. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md)cmdlet. | False | Named | False |
| Description | Specifies the description of the backup copy job. | String | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the VMs added to the job and the target backup repository location do not match. | SwitchParameter | False | Named | False |
| EnableImmediateCopy | Defines that the cmdlet will enable the immediate copy mode.  If you specify this parameter, Veeam Backup & Replication will copy new restore points and logs as soon as they appear.  Otherwise, Veeam Backup & Replication will copy data from backups once per backup copy interval. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Hyper-V Backup Copy Job with WAN Accelerators

|  |  |
| --- | --- |
| This example shows how to create the CopyJob1 Hyper-V backup copy job processed through WAN accelerators.  |  | | --- | | $wansource = Get-VBRWANAccelerator -Name "Sydney WAN"  $wantarget = Get-VBRWANAccelerator -Name "London WAN"  $vms = Find-VBRViEntity -Name "srv2024" -Vm  $repository = Get-VBRBackupRepository -Name "Backups Vol2"  Add-VBRHvBackupCopyJob -SourceAccelerator $wansource -TargetAccelerator $wantarget -Name CopyJob1 -Entity $vms -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $wansource variable. 2. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $wantarget variable. 3. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Provide the Vm parameter. Save the result to the $vms variable. 4. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 5. Run the Add-VBRViBackupCopyJob cmdlet. Specify the following settings:  * Set the $wansource variable as the SourceAccelerator parameter value. * Set the $wantarget variable as the TargetAccelerator parameter value. * Specify the Name parameter value. * Set the $vms variable as the Entity parameter value. * Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Hyper-V Backup Copy Job with Direct Data Transfer

|  |  |
| --- | --- |
| This example shows how to create the DC Backup Hyper-V backup copy job with direct data transfer.  |  | | --- | | Get-VBRBackup -Name "DC Backup" | Add-VBRHvBackupCopyJob -DirectOperation -Name "DC CopyJob" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VBRHvBackupCopyJob cmdlet. Provide the DirectOperation parameter. Specify the Name parameter value. |

Related Commands

* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [Find-VBRHvEntity](find-vbrhventity.md)
* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
