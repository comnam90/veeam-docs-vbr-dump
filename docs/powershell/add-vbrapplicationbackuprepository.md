---
title: "Add-VBRApplicationBackupRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrapplicationbackuprepository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Add-VBRApplicationBackupRepository


Short Description

Adds an application backup repository.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRApplicationBackupRepository -Server <CHost> [-Name <String>] [-Description <String>] -ZFSPool <String> [-MountPath <String>] [-RepositoryPermissions <VBRApplicationBackupRepositoryPermission[]>] [-EnableKerberosPermissions] [-KerberosPermissions <VBRApplicationBackupRepositoryKerberosPermission[]>] [-ScheduleOptions <VBRApplicationBackupRepositoryScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-RetentionDays <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a new application backup repository to the backup infrastructure.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Server | Specifies the server that will host the application backup repository. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Name | Specifies the name you want to assign to the new application backup repository. | String | False | Named | False |
| Description | Specifies the description of the application backup repository. | String | False | Named | False |
| ZFSPool | Specifies the ZFS pool name. | String | True | Named | False |
| MountPath | Specifies the path to the NFS share hosted on the application backup repository. | String | False | Named | False |
| RepositoryPermissions | Specifies host permissions for accessing the NFS share. | Accepts the [VBRApplicationBackupRepositoryPermission](vbrapplicationbackuprepositorypermission.md)[] object. To create this object, run the [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md) cmdlet. | False | Named | False |
| EnableKerberosPermissions | Enables Kerberos authentication for accessing the NFS share. | SwitchParameter | False | Named | False |
| KerberosPermissions | Specifies permissions for accessing the NFS share with Kerberos credentials. | Accepts the [VBRApplicationBackupRepositoryKerberosPermission](vbrapplicationbackuprepositorykerberospermission.md)[] object. To create this object, run the [New-VBRKerberosPermission](new-vbrkerberospermission.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies the schedule settings for the snapshot creation. | Accepts the [VBRApplicationBackupRepositoryScheduleOptions](vbrapplicationbackuprepositoryscheduleoptions.md) object. To get this object, run the [New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings for the snapshot creation. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionDays | Specifies the number of days for the snapshot retention policy. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md) object that contains settings of the application backup repository added to the backup infrastructure.

Examples

Adding Server as Application Backup Repository

This example shows how to add the Repository01 server as a new application backup repository with the following settings:

* The snapshots are created every Friday at 23:00.
* The permissions to access the NFS share are given to the 172.24.26.132 host.

|  |
| --- |
| $server = Get-VBRServer -Name "Repository01"  $permission = -Mode ReadWrite -ServerName 172.24.26.132  $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 23:00  $schedule = New-VBRApplicationBackupRepositoryScheduleOptions -ScheduleEnabled $true -Type Daily -DailyOptions $daily  Add-VBRApplicationBackupRepository -Name "Oracle FRA Repository" -Server $server -ZFSPool "abr01" -RepositoryPermissions $permission -ScheduleOptions $schedule |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md) cmdlet. Specify the Mode and ServerName parameter values. Save the result to the $permission variable.
3. Run the [New-VBRDailyOptions](get-vbrapplicationbackuprepository.md) cmdlet. Specify the DayofWeek and Period parameter values. Save the result to the $daily variable.
4. Run the [New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md) cmdlet. Specify the ScheduleEnabled and Type parameter values. Set the $daily variable as the DailyOptions parameter value. Save the result to the $schedule variable.
5. Run the Add-VBRApplicationBackupRepository cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $server variable as the Server parameter value.
* Specify the ZFSPool parameter value.
* Set the $permission variable as the RepositoryPermissions parameter value.
* Set the $schedule variable as the ScheduleOptions parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md)
* [New-VBRKerberosPermission](new-vbrkerberospermission.md)
* [New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)

Page updated 2026-06-04

