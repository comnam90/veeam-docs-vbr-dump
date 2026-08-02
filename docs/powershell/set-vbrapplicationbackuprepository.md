---
title: "Set-VBRApplicationBackupRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrapplicationbackuprepository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRApplicationBackupRepository


Short Description

Modifies application backup repository settings.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRApplicationBackupRepository -Repository <VBRApplicationBackupRepository> [-Name <String>] [-Description <String>] [-RepositoryPermissions <VBRApplicationBackupRepositoryPermission[]>] [-EnableKerberosPermissions] [-KerberosPermissions <VBRApplicationBackupRepositoryKerberosPermission[]>] [-ScheduleOptions <VBRApplicationBackupRepositoryScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-RetentionDays <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a application backup repository.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Repository | Specifies an application backup repository you want to modify. | Accepts the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md) object. To get this object, run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. | True | Named | False |
| Name | Specifies the name of the application backup repository. | String | False | Named | False |
| Description | Specifies the description of the application backup repository. | String | False | Named | False |
| RepositoryPermissions | Specifies host permissions for accessing the NFS share. | Accepts the [VBRApplicationBackupRepositoryPermission](vbrapplicationbackuprepositorypermission.md)[] object. To create this object, run the [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md) cmdlet. | False | Named | False |
| EnableKerberosPermissions | Enables Kerberos authentication for accessing the NFS share. | SwitchParameter | False | Named | False |
| KerberosPermissions | Specifies permissions for accessing the NFS share with Kerberos credentials. | Accepts the [VBRApplicationBackupRepositoryKerberosPermission](vbrapplicationbackuprepositorykerberospermission.md)[] object. To create this object, run the [New-VBRKerberosPermission](new-vbrkerberospermission.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies the schedule settings for the snapshot creation. | Accepts the [VBRApplicationBackupRepositoryScheduleOptions](vbrapplicationbackuprepositoryscheduleoptions.md) object. To get this object, run the [New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings for the snapshot creation. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionDays | Specifies the number of days for the snapshot retention policy. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md) object that contains settings of the application backup repository.

Examples

Modifying Snapshot Schedule Settings for Application Backup Repository

This example shows how to modify the snapshot creation schedule for the application backup repository named Oracle FRA Repository.

|  |
| --- |
| $repository = Get-VBRApplicationBackupRepository -Name "Oracle FRA Repository"  $options = New-VBRApplicationBackupRepositoryScheduleOptions  Set-VBRApplicationBackupRepository -Repository $repository -ScheduleOptions $options |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md) cmdlet. Save the result to the $options variable.
3. Run the Set-VBRApplicationBackupRepository cmdlet. Set the $repository variable as the Repository parameter value. Set the $options variable as the ScheduleOptions parameter value.

Related Commands

* [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md)
* [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md)
* [New-VBRKerberosPermission](new-vbrkerberospermission.md)
* [New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)

Page updated 2026-06-04

