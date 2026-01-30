---
title: "Using Veeam Backup Validator"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_validator_validate.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Using Veeam Backup Validator


Veeam Backup Validator is located on the backup server in the installation folder of Veeam Backup & Replication — by default, %ProgramFiles%\Veeam\Backup and Replication\Backup\Veeam.Backup.Validator.exe. If the default path was changed, you can find the actual path in the following registry value: [HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication] CorePath.

To run the utility, open the command prompt or the PowerShell console on the backup server and change the current folder to the folder where Veeam Backup Validator is located.

|  |
| --- |
| Important |
| Consider the following:   * To run Veeam Backup Validator, you must use an account with administrative rights on the local machine. Also, you must disable multi-factor authentication (MFA) for this account. For more information, see [Disabling MFA for Service Accounts](mfa.md#disable_mfa_service_accounts). * You cannot use Veeam Backup Validator to verify integrity of [unstructured data backups](unstructured_data_backup.md). * You cannot use Veeam Backup Validator to verify integrity of backups created in Veeam Cloud Connect repositories. For more information on Veeam Cloud Connect repositories, see the [Cloud Repository](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_repository.html?ver=13) section in the Veeam Cloud Connect Guide. * The cloud provider can verify integrity of tenant backups only by using the /file parameter and only if the backup is not encrypted. They cannot verify encrypted backups and they cannot verify backups by using other parameters. * [For backups stored in scale-out backup repositories] Veeam Backup Validator can validate only backups stored in the [performance tier](backup_repository_sobr_extents.md) which consists of backup repositories (except object storage repositories). Make sure that incremental and full backup files are located on the same extent. |

Syntax

Veeam Backup Validator provides parameter sets that allow you to:

* Display Veeam Backup Validator help information.

|  |
| --- |
| Veeam.Backup.Validator /? |

* Validate integrity of the content of all VMs or selected VMs in the specified backup.

|  |
| --- |
| Veeam.Backup.Validator.exe /backup:backupname|backupid [/vmname:vmname] [/point:pointid] [/date:pointdate] [/time:pointtime] [/silence] [/skip] [/report:reportpath [/format:xml|html]] |

* Validate integrity of the VM content in the specified backup file.

|  |
| --- |
| Veeam.Backup.Validator.exe /file:backupfile{1..\*} [/username:username /password:password] [/vmname:vmname]  [/silence] [/skip] [/report:reportpath [/format:xml|html]] |

Parameters

| Parameter | Description | Required/Optional | Parameter Type | Notes |
| --- | --- | --- | --- | --- |
| /backup: | Specifies a name or an ID\* of a backup or backup copy job that you want to validate. | Required | String | Consider the following:   * Per-machine backup with separate metadata files is a default format of backup files. To validate these backup files, you must specify the child backup name — backup of a specific VM. To get the child backup name, use the following PowerShell commands:   |  | | --- | | $backup = Get-VBRBackup -Name "<backup\_name>"  $child\_backups = $backup.FindChildBackups()  $first\_child\_backup\_name = $child\_backups[0].Name |   * For a backup copy job in the immediate mode, you must specify the name of its child job — task that copies backup job [added as a source](backup_copy_vms.md) to the backup copy job. For example, if the My Copy backup copy job copies Daily Backup backup job, then you must set the parameter value to My Copy\Daily Backup.   If you want to validate the whole backup copy job, you must run the utility for each child job. |
| /file:backupfile{1..\*} | Specifies a backup file (VBM, VBK, VIB, VRB) to be validated. | Required | String | Consider the following:   * To validate an incremental backup file, you must specify the whole backup chain starting from the VBK file up to the required incremental file. Each backup file must be specified using a separate /file parameter. * If the file is located on a network share, make sure you specify a full path, for example: \\172.16.16.198\TestShare\Empty VM encryptedD2017-09-22T172639.vbk. * Mapped network drives are not supported. For example, you cannot specify z: \\172.16.16.198\TestShare. |
| /username: username /password: password | To access files on network shares. Specifies account credentials that the utility uses to access network shares. | Required for network share | String | If you want to validate files located on different shares, make sure this account has access rights to all these shares. |
| /vmname:vmname | Specifies a name of the VM in the backup file to be validated. | Optional | String | — |
| /point:pointID | Specifies an ID\* of the restore point to be validated.  Note: You must provide this parameter after the /backup parameter.  To get the restore point ID, run the [Get-VBRRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrestorepoint.html?ver=13) cmdlet and retrieve the PointID property. | Optional | String | If not specified, Veeam Backup Validator will verify the latest restore point, that is, all backup files the restore point consists of. |
| /date:pointdate | Specifies the date when the validated restore point was created. | Optional | Date | Make sure to specify the date in the same format as used on the Veeam Backup server. For example:   * For the mm/dd/yyyy format, specify 08.30.2012. * For the dd/mm/yyyy format, specify 30.08.2012. |
| /time:pointtime | Specifies the approximate time when the validated restore point was created. | Optional | Time | — |
| /silence | Defines whether to run validation in the silence mode. | Optional | Boolean | — |
| /skip | Defines whether to skip from processing VMs listed in the vmname parameter. | Optional | Boolean | In the vmname parameter, list all VMs that you want to skip. |
| /report: reportpath [/format:xml| html] | Specifies a full path of a file where you want to store a report on validation results. The utility will generate a report on validation results and store it at the specified path. | Optional | String | Consider the following:   * You must specify the full file path, for example, "C:\temp\validator-report.html". * Supported report formats are HTML and XML. |

\* You can get IDs of backup jobs and restore points from the Veeam Backup & Replication database using scripts or Management Studio.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Validating Specific VM in Incremental Backup File

|  |  |
| --- | --- |
| This example shows how to validate the winsrv29 VM in the incremental backup file and write the result in the report.html file.  |  | | --- | | Veeam.Backup.Validator.exe /file:"C:\Backup\Backup Job Single Storage\Backup Job Single StorageD2022-10-03T132735\_1E50.vbk" /file:"C:\Backup\Backup Job Single Storage\Backup Job Single StorageD2022-10-28T122338\_3EE4.vib" /vmname:winsrv29 /report:"C:\report.html" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Validating Specific VM Backup

|  |  |
| --- | --- |
| This example shows how to validate the srv506 VM in the Exchange Backup Job backup file.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange Backup Job"  $child\_backups = $backup.FindChildBackups()  $first\_child\_backup\_name = $child\_backups[0].Name  .\Veeam.Backup.Validator /backup:$first\_child\_backup\_name /vmname:srv506 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Validating VM Backup Created After Specific Time and Date

|  |  |
| --- | --- |
| This example shows how to validate the srv506 VM in the Exchange Backup Job backup file created after June 2, 2024, 9:00 PM.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange Backup Job"  $child\_backups = $backup.FindChildBackups()  $first\_child\_backup\_name = $child\_backups[0].Name  .\Veeam.Backup.Validator /backup:$first\_child\_backup\_name /date:02.06.2024 /time:21:00 /vmname:srv506 | |


