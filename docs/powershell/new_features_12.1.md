---
title: "New Features"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new_features_12.1.html"
last_updated: "8/22/2025"
product_version: "13.0.1.1071"
---

# New Features

In this article

This section contains information on new features that were introduced in Veeam PowerShell v12.1.

Security

In this version, you can use new Veeam PowerShell cmdlets to work with security features.

Malware Detection

In this version, you can run new cmdlets to use built-in or third-party malware detection methods to scan backup data and get information about suspicious activity or infected objects.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRObjectRestorePoint](get-vbrobjectrestorepoint.md) | Returns restore points created by jobs. | | [Set-VBRObjectRestorePointStatus](set-vbrobjectrestorepointstatus.md) | Modifies the malware state of restore points. | | [Get-VBRMalwareDetectionObject](get-vbrmalwaredetectionobject.md) | Returns machines affected by malware. | | [Set-VBRMalwareDetectionObjectAsClean](set-vbrmalwaredetectionobjectasclean.md) | Sets clean status for machines and hosts detected with malware. | | [Get-VBRMalwareDetectionOptions](get-vbrmalwaredetectionoptions.md) | Returns malware detection settings. | | [Set-VBRMalwareDetectionOptions](set-vbrmalwaredetectionoptions.md) | Modifies malware detection settings. | | [Export-VBRMalwareDetectionExtensionList](export-vbrmalwaredetectionextensionlist.md) | Exports a list of suspicious files extensions to a certain file. | | [Import-VBRMalwareDetectionExtensionList](import-vbrmalwaredetectionextensionlist.md) | Imports a list of suspicious files extensions from a certain file. | | [Add-VBRMalwareDetectionExclusion](add-vbrmalwaredetectionexclusion.md) | Adds machines to a malware exclusions list. | | [Get-VBRMalwareDetectionExclusion](get-vbrmalwaredetectionexclusion.md) | Returns a list of machines added to malware exclusions. | | [Set-VBRMalwareDetectionExclusion](set-vbrmalwaredetectionexclusion.md) | Modifies notes for a list of machines added to malware exclusions. | | [Remove-VBRMalwareDetectionExclusion](remove-vbrmalwaredetectionexclusion.md) | Removes machines from a malware exclusions list. | | [Get-VBRMalwareDetectionEvent](get-vbrmalwaredetectionevent.md) | Returns malware detection events for machines. | | [Get-VBRYARARule](get-vbryararule.md) | Returns YARA rules. | | [Get-VBRBackupObject](get-vbrbackupobject.md) | Returns backups of VMs. | | [Start-VBRScanbackup](start-vbrscanbackup.md) | Starts a scan of backups with antivirus or YARA scan. | |

Security & Compliance Analyzer

In this version, you can run the [Start-VBRSecurityComplianceAnalyzer](start-vbrsecuritycomplianceanalyzer.md) cmdlet to perform a security check of your backup server configuration.

Data Encryption

In this version, you can run the [New-VBRDecryptionSet](new-vbrdecryptionset.md) cmdet to define security settings, manage encryption keys and decrypt data encrypted with the KMS server.

Configuring Veeam Backup & Replication

Working with KMS Servers

In this version, you can run new cmdlets to work with KMS servers.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRKMSServer](add-vbrkmsserver.md) | Adds KMS servers to the Veeam Backup & Replication console. | | [Get-VBRKMSServer](get-vbrkmsserver.md) | Returns KMS servers added to the Veeam Backup & Replication console. | | [Set-VBRKMSServer](set-vbrkmsserver.md) | Modifies settings of KMS servers. | | [Remove-VBRKMSServer](remove-vbrkmsserver.md) | Removes KMS servers from the Veeam Backup & Replication console. | |

Specifying Syslog Server Settings

In this version, you can run new cmdlets to work with external syslog server.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRSyslogServer](add-vbrsyslogserver.md) | Adds a syslog server to Veeam Backup & Replication. | | [Set-VBRSyslogServer](set-vbrsyslogserver.md) | Modifies syslog server settings. | | [Get-VBRSyslogServer](get-vbrsyslogserver.md) | Returns syslog server settings. | | [Remove-VBRSyslogServer](remove-vbrsyslogserver.md) | Removes a syslog server. | |

Configuring Global VM Exclusions

In this version, you can run new cmdlets to configure global VM exclusions.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRVMExclusion](add-vbrvmexclusion.md) | Adds VMs to global VM exclusions. | | [Get-VBRVMExclusion](get-vbrvmexclusion.md) | Returns a list of global VM exclusions. | | [Set-VBRVMExclusion](set-vbrvmexclusion.md) | Modifies a global VM exclusion. | | [Remove-VBRVMExclusion](remove-vbrvmexclusion.md) | Removes global VM exclusions. | |

Backup Infrastructure Components

Object Storage Repositories

In this version, you can run new cmdlets to perform the following operations:

* To work with S3 compatible object storage with data archiving.
* To roll back checkpoints located in object storage repositories to the previous state.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRS3GlacierCompatibleRepository](add-vbrs3glaciercompatiblerepository.md) | Adds S3 compatible object storage with data archiving to the backup infrastructure. | | [Set-VBRS3GlacierCompatibleRepository](set-vbrs3glaciercompatiblerepository.md) | Modifies settings for Amazon S3 Glacier archive storage added as a backup repository. | | [Sync-VBRObjectStorageRepositoryEntityState](deleted.md) | Rolls back checkpoints located in object storage repositories to the previous state. | |

Scale-Out Backup Repository

In this version, you can run new cmdlets to get backups and restore points stored in archive extents and capacity extents of scale-out backup repositories. Also, you can remove them from scale-out backup repositories using the [Remove-VBRBackup](remove-vbrbackup.md) cmdlet.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md) | Returns backups available in archive extents and capacity extents of scale-out backup repositories. | | [Get-VBRSOBRObjectStorageRestorePoint](get-vbrsobrobjectstoragerestorepoint.md) | Returns restore points stored in archive extents and capacity extents of a scale-out backup repository. | |

Continuous Data Protection (CDP)

In this version, you can use new cmdlets to run restore sessions of guest OS files from a CDP replica.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRCDPWindowsFileRestore](start-vbrcdpwindowsfilerestore.md) | Starts Microsoft Windows guest OS file restore session for a CDP replica. | | [Start-VBRCDPLinuxFileRestore](start-vbrcdplinuxfilerestore.md) | Starts a restore session of Linux-based or Unix-based guest OS files from a CDP replica. | | [New-VBRFileRestoreLinuxHelperApplianceOptions](new-vbrfilerestorelinuxhelperapplianceoptions.md) | Defines configuration settings for a temporary helper appliance. | |

Backup

In this version, you can use new cmdlets to manage background retention for backups.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | Enable-VBRIndependentRetention | Enables previously disabled background retention for backups. | | Disable-VBRIndependentRetention | Disables background retention for backups. | |

SureBackup

In this version, you can use new cmdlets to perform actions with SureBackup jobs that run in the backup content scan verification mode.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRSureBackupContentScanJob](add-vbrsurebackupcontentscanjob.md) | Creates a SureBackup job that run in the backup content scan verification mode. | | [Set-VBRSureBackupContentScanJob](set-vbrsurebackupcontentscanjob.md) | Modifies settings of a SureBackup job that run in the backup content scan verification mode. | |

Unstructured Data Backup

In this version, you can use new cmdlets to back up and restore unstructured data. You can use these cmdlets to perform the following actions:

* Add and manage file shares and object storage as a source of unstructured data.
* Back up content of various file shares and object storage repositories.
* Perform various restore operations of backed-up content.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRAmazonS3Server](add-vbramazons3server.md) | Adds Amazon S3 storage as unstructured data source to the inventory. | | [Set-VBRAmazonS3Server](set-vbramazons3server.md) | Modifies settings of Amazon S3 storage added as unstructured data source to the inventory. | | [Add-VBRAzureBlobServer](add-vbrazureblobserver.md) | Adds Microsoft Azure Blob storage as unstructured data source to the inventory. | | [Set-VBRAzureBlobServer](set-vbrazureblobserver.md) | Modifies settings of Microsoft Azure Blob storage as unstructured data source to the inventory. | | [Add-VBRS3CompatibleServer](add-vbrs3compatibleserver.md) | Adds S3 compatible object storage as unstructured data source to the inventory. | | [Set-VBRS3CompatibleServer](set-vbrs3compatibleserver.md) | Modifies settings of Amazon S3 storage added as unstructured data source to the inventory. | | [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) | Returns unstructured data sources added to the inventory. | | [Remove-VBRUnstructuredServer](remove-vbrunstructuredserver.md) | Removes unstructured data sources from the inventory. | | [Update-VBRUnstructuredBackupPath](update-vbrunstructuredbackuppath.md) | Updates the data source for file backups and object storage backups. | | [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) | Returns file backup jobs and object storage backup jobs. | | [Get-VBRUnstructuredBackupCopyJob](get-vbrunstructuredbackupcopyjob.md) | Returns file backup copy jobs and object storage backup jobs. | | [New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md) | Defines version-based retention policy settings for file backup jobs and object storage backup jobs. | | [Set-VBRUnstructuredBackupVersionRetentionOptions](set-vbrunstructuredbackupversionretentionoptions.md) | Modifies version-based retention policy settings for file backup jobs and object storage backup jobs. | | [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) | Defines a scope of file versions to keep on an archive repository for file backup job or object storage backup job. | | [Set-VBRUnstructuredBackupArchivalOptions](set-vbrunstructuredbackuparchivaloptions.md) | Modifies settings of secondary backup repositories. | | [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) | Creates secondary backup repositories for file backup jobs and object storage backup jobs. | | [Set-VBRUnstructuredBackupSecondaryTarget](set-vbrunstructuredbackupsecondarytarget.md) | Modifies settings of secondary backup repositories. | | [Remove-VBRUnstructuredBackupJob](remove-vbrunstructuredbackupjob.md) | Removes file backup jobs and object storage backup jobs from the backup infrastructure. | | [Get-VBRUnstructuredBackupSession](get-vbrunstructuredbackupsession.md) | Returns backup sessions for file backup jobs and object storage backup jobs. | | [Get-VBRUnstructuredBackupTaskSession](get-vbrunstructuredbackuptasksession.md) | Returns tasks for file share and object storage backup sessions. | | [New-VBRObjectStorageBackupContainerPathMask](new-vbrobjectstoragebackupcontainerpathmask.md) | Defines an exclusion mask for objects in object storage. | | [New-VBRObjectStorageBackupServerPathMask](new-vbrobjectstoragebackupserverpathmask.md) | Defines an exclusion mask for prefixes in object storage. | | [New-VBRObjectStorageBackupTagMask](new-vbrobjectstoragebackuptagmask.md) | Defines a tag mask for objects and prefixes in object storage. | |

Universal Storage API Integrated Systems

In this version, you can use new cmdlets to work with archived snapshots of Universal Storage API integrated systems.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-StoragePluginArchivedSnapshot](get-storagepluginarchivedsnapshot.md) | Returns archived snapshots of Universal Storage API integrated systems. | | [Publish-StoragePluginArchivedSnapshot](publish-storagepluginarchivedsnapshot.md) | Retrieves and restores an archived snapshot. | | [Remove-StoragePluginArchivedSnapshot](remove-storagepluginarchivedsnapshot.md) | Removes archived snapshots of Universal Storage API integrated systems. | |

Veeam Cloud Connect

In this version, you can use new cmdlets to refresh information on the backup and replication resources by a cloud tenant.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Sync-VBRCloudTenantResource](sync-vbrcloudtenantresource.md) | Refreshes information about current usage of backup resources by a cloud tenant. | | [Sync-VBRCloudTenantReplicationResources](sync-vbrcloudtenantteplicationresources.md) | Refreshes information about current usage of the replication resources by a cloud tenant. | |

Tape Devices Support

In this version, you can use new cmdlets to work with object to tape jobs and restore data from tapes.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRObjectToTapeJob](add-vbrobjecttotapejob.md) | Creates an object to tape job. | | [Set-VBRObjectToTapeJob](set-vbrobjecttotapejob.md) | Modifies an object to tape job. | | [Start-VBRTapeObjectStorageRestore](start-vbrtapeobjectstoragerestore.md) | Starts the restore of objects from tape. | |

Veeam Agent Management

In this version, you can use new cmdlets to work with the Veeam Deployer Service certificates for Linux machines.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Generate-VBRBackupServerDeployerKit](generate-vbrbackupserverdeployerkit.md) | Generates the Veeam Deployer Service certificate and installation packages for Microsoft Windows and Linux computers. | | [Get-VBRBackupServerDeployerCertificate](get-vbrbackupserverdeployercertificate.md) | Exports Veeam Deployer Service certificates to the specified location for Linux machines. | | [Remove-VBRBackupServerDeployerCertificate](remove-vbrbackupserverdeployercertificate.md) | Removes Veeam Deployer Service certificates from the Veeam Backup & Replication database. | |

Page updated 8/22/2025

Page content applies to build 13.0.1.1071
