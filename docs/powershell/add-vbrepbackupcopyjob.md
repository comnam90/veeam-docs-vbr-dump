---
title: "Add-VBREPBackupCopyJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrepbackupcopyjob.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Add-VBREPBackupCopyJob (obsolete)


Short Description

|  |
| --- |
| Important |
| This cmdlet is obsolete and only works for creating a simple mode backup copy job. It is recommended to create a new backup job using the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |

Creates backup copy jobs for Veeam Agent operating in a standalone mode.

Syntax

This cmdlet provides parameter sets that allow you to:

* Create backup copy jobs that will transfer data directly.

|  |
| --- |
| Add-VBREpBackupCopyJob -OSPlatform {Windows | Linux | Mac | Unix} -DirectOperation [-Name <string>] [-Description <string>] [-Backup <CBackup[]>] [-BackupJob <VBREPJob[]>] [-SourceRepository <CBackupRepository[]>] [-Repository <CBackupRepository>] [-EnableImmediateCopy] [-Force]  [<CommonParameters>] |

* Create backup copy jobs that will transfer data over WAN accelerators.

|  |
| --- |
| Add-VBREpBackupCopyJob -OSPlatform {Windows | Linux | Mac | Unix} -SourceAccelerator <CWanAccelerator> [-Name <string>] [-Description <string>] [-Backup <CBackup[]>] [-BackupJob <VBREPJob[]>] [-SourceRepository <CBackupRepository[]>] [-Repository <CBackupRepository>] [-TargetAccelerator <CWanAccelerator>] [-EnableImmediateCopy] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates backup copy jobs for Veeam Agent operating in a standalone mode.

Note that the backup copy job is created in a disabled state. Run the [Enable-VBRJob](enable-vbrjob.md) cmdlet to start the job running on the defined schedule.

Run the [Add-VBRComputerBackupCopyJob](add-vbrcomputerbackupcopyjob.md) cmdlet to create backup copy jobs that use Veeam Agent management functionality.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| OSPlatform | Specifies the OS of the  computers where Veeam Agent will operate:   * Windows: for Windows computers. * Linux: for Linux computers. * Mac: for macOS computers. * Unix: for Unix computers. | VBRAgentType | True | Named | False |
| Backup | Specifies the array of backups you want to copy. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| DirectOperation | Used for the direct data transfer.  Enables direct data transfer sending the data directly to the target backup repository without performing data deduplication.  Note that this parameter is required if the WAN acceleration is not used (the SourceAccelerator and TargetAccelerator parameters are not specified). | SwitchParameter | True | Named | False |
| SourceAccelerator | Used for the data transfer using WAN accelerators.  Specifies the WAN accelerator on the source side.  Note that this parameter is required if the Direct Operation is not used (the DirectOperation parameter is not specified). If you specify this parameter and the repository specified in the Repository parameter is not cloud, you must also specify the TargetAccelerator parameter. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| TargetAccelerator | Used for the data transfer using WAN accelerators.  Specifies the WAN accelerator on the target side.  Note that this parameter is required if the WAN acceleration is used (the SourceAccelerator is specified) and the repository specified in the Repository parameter is not cloud. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| Name | Specifies the name you want to assign to the backup copy job.  You can input string up to 255 symbols.  If not set, Veeam Backup & Replication will assign a default backup copy job name. | String | False | Named | False |
| Description | Specifies the description of the backup copy job. | String | False | Named | False |
| BackupJob | Specifies the backup job. The cmdlet will add this job to a backup copy job. | Accepts the [VBREPJob](vbrepjob.md)[] object. To get this object, run the [Get-VBREPJob](get-vbrepjob.md) cmdlet. | False | Named | True (ByPropertyName) |
| Force | Defines that the cmdlet will create backup copy jobs without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| SourceRepository | Specifies an array of source backup repositories. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Repository | Specifies the backup repository to where you want to copy data.  Default: default backup repository. | Accepts CBackupRepository object or string. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableImmediateCopy | Defines that the cmdlet will enable the immediate copy mode.  If you specify this parameter, Veeam Backup & Replication will copy new restore points and logs as soon as they appear.  Otherwise, Veeam Backup & Replication will copy data from backups once per backup copy interval. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* CBackupJob
* [VBREPJob](vbrepjob.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Backup Copy Job with Direct Data Transfer

|  |  |
| --- | --- |
| This example shows how to create a backup copy job with the direct data transfer.  |  | | --- | | $EPbackup = Get-VBRBackup -Name "Backup Job Mediaserver"  $repository = Get-VBRBackupRepository -Name "WinLocal"  Add-VBREpBackupCopyJob -Name "Mediaserver Endpoint Backup Copy" -Description "Mediaserver Endpoint Backup Copy Job" -Backup $EPbackup -DirectOperation -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save it to the $EPbackup variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 3. Run the Add-VBREpBackupCopyJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Specify the Description parameter value. * Set the $EPbackup variable as the Backup parameter value. * Provide the DirectOperation parameter. * Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Backup Copy Job with WAN Accelerators

|  |  |
| --- | --- |
| This example shows how to create a backup copy job using WAN accelerators.  |  | | --- | | $EPbackup = Get-VBRBackup -Name "Backup Job Mediaserver"  $repository = Get-VBRBackupRepository -Name "WinLocal"  $wansource = Get-VBRWANAccelerator -Name "Backup WAN Sydney"  $wantarget = Get-VBRWANAccelerator -Name "Backup WAN London"  Add-VBREPBackupCopyJob -Name "Mediaserver Endpoint Backup Copy" -Description "Mediaserver Endpoint Backup Copy Job" -Backup $EPbackup -Repository $repository -SourceAccelerator $wansource -TargetAccelerator $wantarget |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save it to the $EPbackup variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 3. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet to get a source and a target Wan accelerators. Specify the Name parameter value. Save them to the $wansource and $wantarget variables accordingly. 4. Run the Add-VBREpBackupCopyJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Specify the Description parameter value. * Set the $EPbackup variable as the Backup parameter value. * Set the $repository variable as the Repository parameter value. * Set the $wansource variable as the SourceAccelerator parameter value. * Set the $wantarget variable as the TargetAccelerator parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)


