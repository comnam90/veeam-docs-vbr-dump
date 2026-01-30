---
title: "Start-VBRUnstructuredBackupHealthCheck"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrunstructuredbackuphealthcheck.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Start-VBRUnstructuredBackupHealthCheck


Short Description

Performs a health check of the latest restore point created by file backup jobs and object storage backup jobs and their repair if necessary.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Perform a health check of backup files created by file backup jobs and object storage backup jobs.

|  |
| --- |
| Start-VBRUnstructuredBackupHealthCheck -Backup <VBRUnstructuredBackup[]> [-Force] [-Repair] [-RunAsync]  [<CommonParameters>] |

* Perform a health check for the latest restore point of file backup jobs and object storage backup jobs.

|  |
| --- |
| Start-VBRUnstructuredBackupHealthCheck -Job <CBackupJob[]> [-Repair] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet performs a health check for the latest restore point created by file backup jobs and object storage backup jobs. During the health check, Veeam Backup & Replication performs a CRC check for metadata and a hash check for data blocks in backup files to verify their integrity. If the health check returns notifications of some inconsistencies, you can run the backup repair. To repair the backup, run the cmdlet and provide the Repair parameter.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies backup files created by file backup jobs and object storage backup jobs. The cmdlet will perform a health check for these backup files. | Accepts the VBRUnstructuredBackup[] object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Job | Specifies an array of file backup jobs and object storage backup jobs. The cmdlet will perform a health check for these backup jobs. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Repair | Defines that the cmdlet will repair missing data and metadata.  If you provide this parameter, the cmdlet will repair the missing metadata. Otherwise, the cmdlet will perform a health check of backup files and if corruption is detected, it will return a notification.  Note: First, run the cmdlet with this option disabled to perform the health check. After that, if there are any inconsistencies in the backup, run the cmdlet again with this option enabled. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform a health check without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupHealthCheck object that contains results of a health check for restore points created by file backup jobs and object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Health Check for File Backup Job

|  |  |
| --- | --- |
| This example shows how to perform a health check for a file backup job.  |  | | --- | | $job = Get-VBRUnstructuredBackupJob  Start-VBRUnstructuredBackupHealthCheck -Job $job |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Save the result to the $job variable. 2. Run the Start-VBRUnstructuredBackupHealthCheck cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Backup Repair

|  |  |
| --- | --- |
| This example shows how to perform a repair of corrupted data if the previously run health check detects them.  |  | | --- | | $job = Get-VBRUnstructuredBackupJob  Start-VBRUnstructuredBackupHealthCheck -Job $job -Repair |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Save the result to the $job variable. 2. Run the Start-VBRUnstructuredBackupHealthCheck cmdlet. Set the $job variable as the Job parameter value. Provide the Repair parameter. |

Related Commands

[Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md)


