---
title: "Convert-VBRLegacyCopyBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/convert-vbrlegacycopybackup.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Convert-VBRLegacyCopyBackup


Short Description

Converts legacy backup file of legacy periodic backup copy job to the per-machine backup with separate metadata files using mapping.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Convert-VBRLegacyCopyBackup -Backup <CBackup> [-Days <Int32>] [-EnableTimeBasedRetention] [-RunAsync] -TargetJob <VBRBackupCopyJob>  [<CommonParameters>] |

Detailed Description

This cmdlet converts legacy backup file of legacy periodic backup copy job to the per-machine backup with separate metadata files format using synthetic full creation based on the old backup file.

The cmdlet detaches legacy backup file from legacy periodic backup copy job and links the new backup file to the new backup copy job. After you run the cmdlet, you will have two backups: detached legacy backup file (in orphaned node) and per-machine backup with separate metadata files linked to the new backup copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies backup file. The cmdlet will return the backup file you want to link to the new backup copy job. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByValue) |
| TargetJob | Specifies a backup copy job to which you want to map a backup file. | Accepts the VBRBackupCopyJob object. To create this object, run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. | True | Named | False |
| Days | Specifies an amount of days after which detached legacy backup file is deleted from the storage.  Note: Days count starts from the backup storage creation date. | Int32 | False | Named | False |
| EnableTimeBasedRetention | Defines that retention policy is applied to the source legacy backup file and its incremental backup files. The amount of retention days is specified in the Days parameter.  When determining whether the number of days is exceeded, the cmdlet compares storage creation date, the current date and retention days.  Note: If the number of retention days is exceeded for the source legacy backup file but not exceeded for any of the incremental backup files, the source legacy backup file will not be deleted. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Upgrading Backup Chain Format

This example shows how to simplify the backup chain format upgrade process.

|  |
| --- |
| Important |
| By following this example, you will detach legacy backup file from legacy periodic backup copy job and link the new backup file to the newly created backup copy job. You may need to edit this example script with details that are relevant to your backup infrastructure (GFS retention settings, notification settings and so on). |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 1. Getting Job Name and Target Repository

|  |  |
| --- | --- |
| At this step, get the job name and the target repository.  |  | | --- | | $LegacyJobName = "LegacyCopyJobName"  $Repo = Get-VBRBackupRepository -Name "TargetRepoName" # provide -ScaleOut parameter if it is a scale-out backup repository |  Perform the following steps:   1. Specify the job name. Save the result to the $LegacyJobName variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Provide the ScaleOut parameter if your target repository is a scale-out repository. Save the result to the $Repo variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 2. Specifying Job and Repository Settings

|  |  |
| --- | --- |
| At this step, specify the job and the repository settings.  |  | | --- | | $LegacyJob = Get-VBRJob -Name $LegacyJobName  $LegacyBackup = Get-VBRBackup -Name $LegacyJob.name  $NewJobName = ($LegacyJob.name + "\_Upgraded") |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Set the $LegacyJobName variable as the Name parameter value. Save the result to the $LegacyJob variable. 2. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Set the $LegacyJob.name variable as the Name parameter value. Save the result to the $LegacyBackup variable. 3. Use the ($LegacyJob.name + "\_Upgraded") command to create a name for the job that will contain upgraded backups. Save the result to the $NewJobName variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 3. Getting Legacy Backup Copy Job Source Objects and Disabling Job

|  |  |
| --- | --- |
| At this step, get legacy backup copy job source objects and disable the job you want to upgrade.  |  | | --- | | $Sources = Get-VBRLegacyBackupCopySourceJob -Job $LegacyJob  Disable-VBRJob -Job $LegacyJob |  Perform the following steps:   1. Run the [Get-VBRLegacyBackupCopySourceJob](get-vbrlegacybackupcopysourcejob.md) cmdlet. Set the $LegacyJob variable as the Job parameter value. Save the result to the $Sources variable. 2. Run the [Disable-VBRJob](disable-vbrjob.md) cmdlet. Set the $LegacyJob variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 4. Getting Legacy Source Backup Files and Starting Upgrade Process

|  |  |
| --- | --- |
| At this step, get legacy source backups files you want to upgrade to the per-machine backups with separate metadata files. Validate which of them are eligible for the upgrade using the foreach statement and start the upgrade process. Any existing per-machine backups with separate metadata files will be skipped.  |  | | --- | | $SourceJobName = $Sources.name  $SourceBackups = Get-VBRBackup -Name $SourceJobName  foreach ($SourceBackup in $SourceBackups)  {                      if ($SourceBackup.istruepervmcontainer -eq $True)                   {                            write-host ("Backup "+$SourceJobName+" is already upgraded")                   }                      else                      {                            Upgrade-VBRBackup -Backup $SourceBackup -Force                   }               } |  Perform the following steps:   1. Assign the $sources.name variable as the $SourceJobName variable value. 2. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Set the $SourceJobName variable as the Name parameter value. Save the result to the $SourceBackups variable. 3. Use the foreach statement where the $SourceBackup variable represents legacy source backup files and the $SourceBackups variable represents the collection of these files. Provide the If Else statements from the example. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Step 5. Adding New Backup Copy Job and Converting Legacy Backup Files

|  |  |
| --- | --- |
| At this step, add new backup copy job and convert legacy backup files to the per-machine backups with separate metadata files.  |  | | --- | | $NewBackupCopyJob = Add-VBRBackupCopyJob -Name $NewJobName -Mode Immediate -BackupJob $Sources -TargetRepository $Repo -DirectOperation  Convert-VBRLegacyCopyBackup -Backup $LegacyBackup -TargetJob $NewBackupCopyJob |  Perform the following steps:   1. Run the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. Set the $NewJobName variable as the Name parameter value. Specify the Mode, the BackupJob and the TargetRepository parameter values. Provide the DirectOperation parameter. Save the result to the $NewBackupCopyJob variable. 2. Run the Convert-VBRLegacyCopyBackup cmdlet. Set the $LegacyBackup variable as the Backup parameter value. Set the $NewBackupCopyJob variable as the TargetJob parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Full Script Example

|  |  |
| --- | --- |
| |  | | --- | | $LegacyJobName = "LegacyCopyJobName"  $Repo = Get-VBRBackupRepository -Name "LegacyCopyJobTargetRepoName" # provide -ScaleOut parameter if it is a scale-out backup repository    $LegacyJob = Get-VBRJob -Name $LegacyJobName  $LegacyBackup = Get-VBRBackup -Name $LegacyJob.name  $NewJobName = ($LegacyJob.name + "\_Upgraded")    $Sources = Get-VBRLegacyBackupCopySourceJob -Job $LegacyJob  Disable-VBRjob -Job $LegacyJob                         $SourceJobName = $Sources.name  $SourceBackups = Get-VBRBackup -Name $SourceJobName  foreach ($SourceBackup in $SourceBackups)  {                      if ($SourceBackup.istruepervmcontainer -eq $True)                   {                            write-host ("Backup "+$SourceJobName+" is already upgraded")                   }                      else                      {                            Upgrade-VBRBackup -Backup $SourceBackup -Force                   }               }                 $NewBackupCopyJob = Add-VBRBackupCopyJob -Name $NewJobName -Mode Immediate -BackupJob $Sources -TargetRepository $Repo -DirectOperation  Convert-VBRLegacyCopyBackup -Backup $LegacyBackup -TargetJob $NewBackupCopyJob | |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRLegacyBackupCopySourceJob](get-vbrlegacybackupcopysourcejob.md)
* [Disable-VBRJob](disable-vbrjob.md)
* [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md)


