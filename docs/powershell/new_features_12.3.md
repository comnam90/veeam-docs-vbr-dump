---
title: "New Features"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new_features_12.3.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# New Features

In this article

This section contains information on new features that were introduced in Veeam PowerShell v12.3.

Security

In this version, you can run new cmdlets to manage and limit a number of syslog events.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRSyslogEventFilter](add-vbrsyslogeventfilter.md) | Adds a syslog event filter for an event ID. | | [Get-VBRSyslogEventFilters](get-vbrsyslogeventfilters.md) | Returns the list of syslog event filters. | | [Remove-VBRSyslogEventFilter](remove-vbrsyslogeventfilter.md) | Removes syslog event filters for an event ID. | |

Backup Infrastructure

In this version, you can run new cmdlets to work with 11:11 Cloud Object Storage.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBR1111SystemsS3Repository](add-vbr1111systemss3repository.md) | Adds 11:11 Cloud Object Storage to the backup infrastructure. | | [Set-VBR1111SystemsS3Repository](set-vbr1111systemss3repository.md) | Modifies settings of 11:11 Cloud Object Storage added to the backup infrastructure. | |

Data Recovery

Guest OS File Recovery

In this version, you can run new cmdlets to create and manage temporary Linux helper host for the guest OS file restore.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRLinuxFileRestoreHelperHost](new-vbrlinuxfilerestorehelperhost.md) | Creates temporary Linux helper host used to launch the guest OS file restore. | | [Set-VBRLinuxFileRestoreHelperHost](set-vbrlinuxfilerestorehelperhost.md) | Modifies temporary Linux helper host specifications. | |

Virtual Disks Restore

In this version, you can run the [New-VBRHvVirtualDeviceMappingRule](new-vbrhvvirtualdevicemappingrule.md) cmdlet to define the backed-up virtual disk mapping settings.

Microsoft EntraID Support

In this version, you can run new cmdlets to back up and restore data for Microsoft Entra ID tenants by means of Veeam PowerShell.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBREntraIDTenant](add-vbrentraidtenant.md) | Adds a Microsoft Entra ID tenant to the backup infrastructure. | | [Get-VBREntraIDTenant](get-vbrentraidtenant.md) | Returns Microsoft Entra ID tenants added to the Veeam Backup & Replication backup infrastructure. | | [Set-VBREntraIDTenant](set-vbrentraidtenant.md) | Modifies a Microsoft Entra ID tenant added to the backup infrastructure. | | [Remove-VBREntraIDTenant](remove-vbrentraidtenant.md) | Removes Microsoft Entra ID tenants from the backup infrastructure. | | [Start-VBREntraIDDBRepositoryRescan](start-vbrentraiddbrepositoryrescan.md) | Starts rescan of the repository where the Microsoft Entra ID tenant backups are stored. | | [New-VBREncryptionOptions](new-vbrencryptionoptions.md) | Defines encryption settings. | | [Add-VBREntraIDTenantBackupJob](add-vbrentraidtenantbackupjob.md) | Creates a backup job that protects a Microsoft Entra ID tenant. | | [Start-VBREntraIDTenantBackupJob](start-vbrentraidtenantbackupjob.md) | Starts backup jobs that protect Microsoft Entra ID tenants. | | [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) | Returns backup jobs that protect Microsoft Entra ID tenants. | | [Set-VBREntraIDTenantBackupJob](set-vbrentraidtenantbackupjob.md) | Modifies a backup job that protects a Microsoft Entra ID tenant. | | [Remove-VBREntraIDTenantBackupJob](remove-vbrentraidtenantbackupjob.md) | Removes backup jobs that protect Microsoft Entra ID tenants. | | [Stop-VBREntraIDTenantBackupJob](stop-vbrentraidtenantbackupjob.md) | Stops running backup jobs that protect Microsoft Entra ID tenants. | | [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) | Returns backups of Microsoft Entra ID tenants. | | [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) | Returns Microsoft Entra ID items that were backed up. | | [Add-VBREntraIDLogsBackupJob](add-vbrentraidlogsbackupjob.md) | Creates a Microsoft Entra ID log backup job. | | [Get-VBREntraIDLogsBackupJob](get-vbrentraidlogsbackupjob.md) | Returns Microsoft Entra ID log backup jobs. | | [Set-VBREntraIDLogsBackupJob](set-vbrentraidlogsbackupjob.md) | Modifies a Microsoft Entra ID log backup job. | | [Remove-VBREntraIDLogsBackupJob](remove-vbrentraidlogsbackupjob.md) | Removes Microsoft Entra ID log backup jobs. | | [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) | Returns backups of Microsoft Entra ID logs. | | [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) | Starts a restore session for a Microsoft Entra ID tenant. | | [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) | Returns restore sessions started to recover Microsoft Entra ID tenant backups. | | [Stop-VBREntraIDTenantRestore](stop-vbrentraidtenantrestore.md) | Stops a Microsoft Entra ID tenant restore session. | | [Request-VBREntraIDLogin](request-vbrentraidlogin.md) | Requests login to Microsoft Entra ID using an account associated with the tenant whose data you are restoring. | | [Validate-VBREntraIDTenantItem](validate-vbrentraidtenantitem.md) | Validates that a restore point contains data for the specified Microsoft Entra ID items. | | [Generate-VBREntraIDTenantUserPassword](generate-vbrentraidtenantuserpassword.md) | Creates passwords. | | [New-VBREntraIDUserCredentials](new-vbrentraidusercredentials.md) | Defines an object that matches a Microsoft Entra ID user and a password. | | [Restore-VBREntraIDTenantItem](restore-vbrentraidtenantitem.md) | Restores a Microsoft Entra ID item. | | [Get-VBREntraIDTenantItemRestoreSession](get-vbrentraidtenantitemrestoresession.md) | Returns a restore session launched for the item or attribute restore. | | [Stop-VBREntraIDTenantItemRestoreSession](stop-vbrentraidtenantitemrestoresession.md) | Stops a session launched to restore Microsoft Entra ID items or their attributes. | | [Compare-VBREntraIDTenantItem](compare-vbrentraidtenantitem.md) | Compares backed-up objects between two restore points or a restore point and the production state. | | [New-VBREntraIDTenantItemIncludedProperty](new-vbrentraidtenantitemincludedproperty.md) | Defines an object with item properties or references that you want to restore. | | [Restore-VBREntraIDTenantItemAttributes](restore-vbrentraidtenantitemattributes.md) | Restores properties of Microsoft Entra ID items. | | [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) | Starts a restore session to explore log files and folders that a log backup contains. | | [Get-VBREntraIDLogsBackupFLRItem](get-vbrentraidlogsbackupflritem.md) | Returns backed-up objects created by a log backup job. | | [Stop-VBREntraIDLogsBackupFLRSession](stop-vbrentraidlogsbackupflrsession.md) | Stops a restore session started to recover data from Microsoft Entra ID log backups. | | [Save-VBREntraIDLogsBackupFLRItem](save-vbrentraidlogsbackupflritem.md) | Restores files and folders backed up by a log backup job that protects Microsoft Entra ID audit and sign-in logs. | |

Veeam VM Migrator

In this version, you can run new cmdlets to resolve MORef ID misalignment after VMware vCenter migration.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Set-VBRVmBiosUuid](set-vbrvmbiosuuid.md) | Collects MORef IDs. | | [Set-VBRVCenterName](set-vbrvcentername.md) | Modifies VMware vCenter name. | | [Generate-VBRViMigrationSpecificationFile](generate-vbrvimigrationspecificationfile.md) | Generates a migration task file. | | [Start-VBRViVMMigration](start-vbrvivmmigration.md) | Starts the MORef ID update. | |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
