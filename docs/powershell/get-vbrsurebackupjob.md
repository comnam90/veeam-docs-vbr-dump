---
title: "Get-VBRSureBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsurebackupjob.html"
last_updated: "4/26/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSureBackupJob

In this article

Short Description

Returns SureBackup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Getting SureBackup jobs by the job name.

|  |
| --- |
| Get-VBRSureBackupJob [-Name <string[]>]  [<CommonParameters>] |

* Getting SureBackup jobs by the job ID.

|  |
| --- |
| Get-VBRSureBackupJob [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns SureBackup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for SureBackup jobs. The cmdlet will return SureBackup jobs with these names. | String[] | True | Named | True (ByValue, |
| Id | Specifies an array of IDs for SureBackup jobs. The cmdlet will return SureBackup jobs with these IDs. | Guid[] | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupJob object that contains settings of SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All SureBackup Jobs from Veeam Backup & Replication Infrastructure

|  |  |
| --- | --- |
| This command returns all SureBackup jobs that are added to the Veeam Backup & Replication Infrastructure. The cmdlet output will contain details on SureBackup jobs.  |  | | --- | | Get-VBRSureBackupJob  VirtualLab                  : Virtual Lab 2  ApplicationGroup            : Application Group 2  KeepApplicationGroupRunning : True  LinkedJob                   : {Veeam.Backup.PowerShell.Infos.VBRSureBackupLinkedJob}  LinkToJobs                  : True  MaxConcurrentVMs            : 3  VerificationOptions         : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobVerificationOptions  ScheduleOptions             : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobScheduleOptions  LastRun                     : 2/28/2020 6:31:24 AM  LastResult                  : None  NextRun                     : 1/1/0001 12:00:00 AM  LastState                   : Starting  IsEnabled                   : True  ScheduleEnabled             : True  Id                          : 1982ee0c-acd2-4c7c-a97f-e8d8cafabf31  Name                        : Job02  Description                 : Created by WinSRV2049\Administrator at 2/20/2020 6:23 AM.    VirtualLab                  : Virtual Lab 1  ApplicationGroup            : Application Group 1  KeepApplicationGroupRunning : True  LinkedJob                   : {}  LinkToJobs                  : False  MaxConcurrentVMs            : 3  VerificationOptions         : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobVerificationOptions  ScheduleOptions             : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobScheduleOptions  LastRun                     : 2/25/2020 6:22:39 AM  LastResult                  : None  NextRun                     : 1/1/0001 12:00:00 AM  LastState                   : Working  IsEnabled                   : True  ScheduleEnabled             : True  Id                          : 6298815d-2c1c-46a0-86a9-299a8bf1ab72  Name                        : Job01  Description                 : Created by WinSRV2049\Administrator at 2/20/2020 6:21 AM. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SureBackup Job by Name

|  |  |
| --- | --- |
| This command returns the SureJob2 SureBackup job. The cmdlet output will contain details on the SureBackup job.  |  | | --- | | Get-VBRSureBackupJob -Name "SureJob2"  VirtualLab                  : Virtual Lab 2  ApplicationGroup            : Application Group 2  KeepApplicationGroupRunning : True  LinkedJob                   : {Veeam.Backup.PowerShell.Infos.VBRSureBackupLinkedJob}  LinkToJobs                  : True  MaxConcurrentVMs            : 3  VerificationOptions         : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobVerificationOptions  ScheduleOptions             : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobScheduleOptions  LastRun                     : 9/24/2019 6:31:24 AM  LastResult                  : None  NextRun                     : 1/1/0001 12:00:00 AM  LastState                   : Starting  IsEnabled                   : True  ScheduleEnabled             : True  Id                          : 1982ee0c-acd2-4c7c-a97f-e8d8cafabf31  Name                        : Job02  Description                 : Created by WinSRV2049\Administrator at 2/20/2020 6:23 AM. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting SureBackup Job by ID

|  |  |
| --- | --- |
| This command returns the 6298815d-2c1c-46a0-86a9-299a8bf1ab72 SureBackup job. The cmdlet output will contain details on the SureBackup job.  |  | | --- | | Get-VBRSureBackupJob -Id 6298815d-2c1c-46a0-86a9-299a8bf1ab72  VirtualLab                  : Virtual Lab 1  ApplicationGroup            : Application Group 1  KeepApplicationGroupRunning : True  LinkedJob                   : {}  LinkToJobs                  : False  MaxConcurrentVMs            : 3  VerificationOptions         : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobVerificationOptions  ScheduleOptions             : Veeam.Backup.PowerShell.Infos.VBRSureBackupJobScheduleOptions  LastRun                     : 9/24/2019 6:22:39 AM  LastResult                  : None  NextRun                     : 1/1/0001 12:00:00 AM  LastState                   : Working  IsEnabled                   : True  ScheduleEnabled             : True  Id                          : 6298815d-2c1c-46a0-86a9-299a8bf1ab72  Name                        : Job01  Description                 : Created by WinSRV2049\Administrator at 2/20/2020 6:21 AM. | |

Page updated 4/26/2024

Page content applies to build 13.0.1.1071
