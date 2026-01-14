---
title: "New and Updated Cmdlets"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new_updated_cmdlets.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New and Updated Cmdlets

In this article

This section contains information on updated cmdlets and new cmdlets that were introduced in Veeam PowerShell v12.

Backup

In Veeam PowerShell v12, cmdlets that apply to backup management were extended and updated.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Copy-VBRBackup](copy-vbrbackup.md) | Copies backups to a repository or local or shared folder. | | [Detach-VBRBackup](detach-vbrbackup.md) | Detaches backups from the job they belong to. | | [Get-VBRGoogleCloudBackup](get-vbrgooglecloudbackup.md) | Returns backups of Google Cloud VM instances. | | [Move-VBRBackup](move-vbrbackup.md) | Moves all backups of a job to another repository or specific workloads and their backups to another job. | | [Upgrade-VBRBackup](upgrade-vbrbackup.md) | Upgrades the storage format of backups from per-machine with single metadata file to per-machine with separate metadata files. | | [Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md) | Returns an array of backup files deleted from the archive tier and preserved by insider protection. | | [Download-VBRDeletedArchivedBackupFile](download-vbrdeletedarchivedbackupfile.md) | Retrieves a backup file deleted from the archive tier and preserved by insider protection. | | [Get-VBRDeletedDehydratedBackupFile](get-vbrdeleteddehydratedbackupfile.md) | Returns a list of backup files deleted from the capacity tier and preserved by insider protection. | | [Rehydrate-VBRDeletedBackupFile](rehydrate-vbrdeletedbackupfile.md) | Rehydrates a backup file deleted from the capacity tier and preserved by insider protection. | | [Get-VBRCloudTenantBackup](get-vbrcloudtenantbackup.md) | Returns non-encrypted backups of AD tenants and tenants managed by the Service Provider. | | [Get-VBRCloudTenantRestorePoint](get-vbrcloudtenantrestorepoint.md) | Returns restore points of non-encrypted backups for AD tenants and tenants managed by the Service Provider. | |

Backup Copy

In Veeam PowerShell v12, cmdlets that apply to backup copy were extended and updated.

For more information, see [Backup Copy](https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy.html?ver=13).

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) | Creates a backup copy job. | | [Convert-VBRLegacyCopyBackup](convert-vbrlegacycopybackup.md) | Converts legacy backup file of legacy periodic backup copy job to the per-machine backups with separate metadata files using mapping. | | [Copy-VBRBackupCopyJob](copy-vbrbackupcopyjob.md) | Copies a backup copy job. | | [Disable-VBRBackupCopyJob](disable-vbrbackupcopyjob.md) | Disables a backup copy job. | | [Enable-VBRBackupCopyJob](enable-vbrbackupcopyjob.md) | Enables a backup copy job. | | [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) | Returns a backup copy job. | | [Get-VBRLegacyBackupCopySourceJob](get-vbrlegacybackupcopysourcejob.md) | Returns legacy periodic backup copy job source objects. | | [Remove-VBRBackupCopyJob](remove-vbrbackupcopyjob.md) | Removes a backup copy job. | | [Set-VBRBackupCopyJob](set-vbrbackupcopyjob.md) | Modifies a backup copy job. | |

Backup Infrastructure

In Veeam PowerShell v12, cmdlets that apply to backup infrastructure were extended and updated.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Add-VBRBackupRepository](add-vbrbackuprepository.md) | Parameters added: AutoSelectGateway, RotatedDriveCleanupMode | | [Add-VBRCredentials](add-vbrcredentials.md) | Allows to add Group Managed Service Accounts (gMSAs). | | [Export-VBRLogs](export-vbrlogs.md) | Parameters removed: From, To. | | [Export-VBRRestorePoint](export-vbrrestorepoint.md) | Parameter added: Repository. | | [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) | Parameter added: PostgreSQL. | |

Continuous Data Protection (CDP) for VMware Cloud Director

In Veeam PowerShell v12, cmdlets that apply to CDP were extended and updated.

For more information on CDP for VMware Cloud Director, see [CDP for VMware Cloud Director](https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_cdp.html?ver=13).

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Add-VBRvCDCDPPolicy](add-vbrvcdcdppolicy.md) | Creates a Cloud Director CDP policy. | | [Disable-VBRCDPPolicy](disable-vbrcdppolicy.md) | Disables Cloud Director CDP policies. | | [Enable-VBRCDPPolicy](enable-vbrcdppolicy.md) | Enables Cloud Director CDP policies. | | [Get-VBRCDPPolicy](get-vbrcdppolicy.md) | Returns Cloud Director CDP policies. | | [Get-VBRCDPReplica](get-vbrcdpreplicavcd.md) | Returns Cloud Director CDP replicas. | | [Get-VBRvCDCDPFilter](get-vbrvcdcdpfilter.md) | Returns a list of Veeam I/O filter installed on an ESXi host. | | [Get-VBRvCDCDPLongTermRestorePoint](get-vbrvcdcdplongtermrestorepoint.md) | Returns long-term restore points of a Cloud Director CDP replica. | | [Get-VBRvCDCDPShortTermRestoreInterval](get-vbrvcdcdpshorttermrestoreinterval.md) | Returns short-term restore points of a Cloud Director CDP replica. | | [Install-VBRvCDCDPFilter](install-vbrvcdcdpfilter.md) | Installs Veeam I/O filter on organization VDCs. | | [Remove-VBRCDPPolicy](remove-vbrcdppolicy.md) | Removes Cloud Director CDP policies. | | [Remove-VBRCDPReplica](remove-vbrcdpreplicavcd.md) | Removes a Cloud Director CDP replica. | | [Set-VBRvCDCDPPolicy](set-vbrvcdcdppolicy.md) | Modifies a Cloud Director CDP policy. | | [Start-VBRvCDCDPReplicaFailback](start-vbrvcdcdpreplicafailback.md) | Starts to perform failback from a Cloud Director CDP replica to the production vApp. | | [Start-VBRvCDCDPReplicaFailover](start-vbrvcdcdpreplicafailover.md) | Starts to perform failover to a Cloud Director CDP replica. | | [Stop-VBRvCDCDPReplicaFailback](stop-vbrvcdcdpreplicafailback.md) | Stops Cloud Director CDP replica failback. | | [Stop-VBRvCDCDPReplicaFailover](stop-vbrvcdcdpreplicafailover.md) | Stops Cloud Director CDP replica failover. | | [Uninstall-VBRvCDCDPFilter](uninstall-vbrvcdcdpfilter.md) | Removes Veeam I/O filter from organization VDCs. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Add-VBRCDPProxy](add-vbrcdpproxy.md) | Parameter added: CacheSizeUnit. | | [Get-VBRCDPSession](get-vbrcdpsession.md) | Type updated for the Policy parameter: changed from the VBRCDPPolicy type to the VBRCDPPolicyBase type. | | [Remove-VBRCDPReplica](remove-vbrcdpreplica.md) | Type updated for the Replica parameter: changed from the VBRCDPReplica to the VBRCDPReplicaBase type. | | [Set-VBRCDPProxy](set-vbrcdpproxy.md) | Parameter added: CacheSizeUnit. | |

Continuous Data Protection (CDP) with Veeam Cloud Connect

In Veeam PowerShell v12, cmdlets that apply to CDP with Veeam Cloud Connect were extended and updated.

For more information on CDP with Veeam Cloud Connect, see the [Continuous Data Protection (CDP) with Veeam Cloud Connect](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_cdp.html?ver=120) section of the Veeam Cloud Connect Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Add-VBRCloudCDPPolicy](add-vbrcloudcdppolicy.md) | Creates a cloud CDP policy. | | [Add-VBRvCDCloudCDPPolicy](add-vbrvcdcloudcdppolicy.md) | Creates a VDC CDP policy. | | [Get-VBRViCloudVM](get-vbrvicloudvm.md) | Returns VMs available in cloud hosts allocated by cloud resources. | | [Set-VBRvCDCloudCDPPolicy](set-vbrvcdcloudcdppolicy.md) | Modifies a VDC CDP policy. | | [Set-VBRCloudCDPPolicy](set-vbrcloudcdppolicy.md) | Modifies a cloud CDP policy. | |

Data Recovery

In Veeam PowerShell v12, cmdlets that apply to data recovery were extended and updated.

For more information, see the [Instant Recovery to Microsoft Hyper-V](https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_to_hv.html?ver=13) section in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [New-VBRHvInstantRecoveryHelperAppliance](new-vbrhvinstantrecoveryhelperappliance.md) | Defines settings for a helper appliance. | | [New-VBRHvInstantRecoveryNetworkMappingRule](new-vbrhvinstantrecoverynetworkmappingrule.md) | Creates a new network mapping rule. | | [Set-VBRHvInstantRecoveryHelperAppliance](set-vbrhvinstantrecoveryhelperappliance.md) | Modifies settings for a helper appliance. | | [Mount-VBRWindowsFileRestoreItems](mount-vbrwindowsfilerestoreitems.md) | Mounts disks of VMs for which restore is launched to the Veeam Backup & Replication console. | | [Stop-VBRLinuxGuestItemRestore](stop-vbrlinuxguestitemrestore.md) | Stops Linux guest OS file restore session. | | [Stop-VBRWindowsGuestItemRestore](stop-vbrwindowsguestitemrestore.md) | Stops Windows guest OS file restore session. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Copy-VBRLinuxGuestItem](copy-vbrlinuxguestitem.md) | Parameter added: ShareCredentials. | | [Copy-VBRWindowsGuestItem](copy-vbrwindowsguestitem.md) | Parameters added: FileRestore, ShareCredentials, Session. | | [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md) | Parameters added: ChangedOnly, CompareWithOriginal, FileRestore, RunAsync.  Parameters updated: Session changed from required to non-required. | | [Start-VBRHvInstantRecovery](start-vbrhvinstantrecovery.md) | Parameters added: NetworkMapping, HelperAppliance, DisableDiskAllocation. | | [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) | Parameters added: ChangedItemsOnly, FileRestore, PermissionsOnly, RunAsync, TargetDirectory, TargetHvVm, TargetVcdVm, TargetViVm. | |

Google Cloud

In Veeam PowerShell v12, cmdlets that apply to Google Cloud object storage repository were extended and updated.

For more information, see the [Adding Google Cloud Object Storage](https://helpcenter.veeam.com/docs/vbr/userguide/adding_google_cloud_object_storage.html?ver=13) section of the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md) | Adds Google Cloud object storage repository to Veeam Backup & Replication. | | [Set-VBRGoogleCloudRepository](set-vbrgooglecloudrepository.md) | Modifies settings for Google Cloud object storage repository added to Veeam Backup & Replication. | |

Jobs

In Veeam PowerShell v12, cmdlets that apply to jobs management were extended and updated.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Install-VBRLinuxTransportService](install-vbrlinuxtransportservice.md) | Installs Veeam Data Mover for guest processing on Linux VMs. | | [Retry-VBRCopyBackupSession](retry-vbrcopybackupsession.md) | Retries the copy operation for failed workloads. | | [Retry-VBRMoveBackupSession](retry-vbrmovebackupsession.md) | Retries the move operation for failed workloads. | | [Uninstall-VBRLinuxTransportService](uninstall-vbrlinuxtransportservice.md) | Uninstalls guest processing Veeam Data Mover from Linux VMs. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Get-VBRBackupSession](get-vbrbackupsession.md) | Parameter added: Id. | | [Get-VBRSession](get-vbrsession.md) | Parameter added: Type. | | [New-VBRNotificationOptions](new-vbrnotificationoptions.md) | Parameters added: EnableDailyNotification, SendTime. | | [Start-VBRJob](start-vbrjob.md) | Parameter added: Object. | |

File Backup

In Veeam PowerShell v12, cmdlets that apply to file backup were extended and updated.

For more information, see the [Unstructured Data](https://helpcenter.veeam.com/docs/vbr/userguide/unstructured_data_backup.html?ver=13) section in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Copy-VBRNASBackup](copy-vbrnasbackup.md) | Copies file share backups to another repository or local or shared folder. | | [Disable-VBRNASProxyServer](disable-vbrnasproxyserver.md) | Disables an enabled file share backup proxy. | | [Enable-VBRNASProxyServer](enable-vbrnasproxyserver.md) | Enables a disabled file share backup proxy. | | [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md) | Returns active sessions of migration to production during the instant file share recovery. | | [Get-VBRNASObjectStorageTransformThreshold](get-vbrnasobjectstoragetransformthreshold.md) | Returns the blob transformation threshold defined for an object storage repository that stores file backups. | | [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md) | Defines the switchover parameter that can be used when starting the file share migration session or for changing settings of an already running file share migration session. | | [Set-VBRNASInstantRecoveryMigration](set-vbrnasinstantrecoverymigration.md) | Modifies switchover parameters for the specified session of migration to production during the instant file share recovery. | | [Start-VBRNASInstantRecoveryMigration](start-vbrnasinstantrecoverymigration.md) | Starts migration to production for the running instant file share recovery session. | | [Switch-VBRNASInstantRecoveryMigration](switch-vbrnasinstantrecoverymigration.md) | Starts the manual switchover for completing the migration to production after you perform the instant file share recovery. | | [Set-VBRNASObjectStorageTransformThreshold](set-vbrnasobjectstoragetransformthreshold.md) | Modifies the blob transformation threshold for an object storage repository that stores file backups. | | [Sync-VBRNASBackupState](deleted.md) | Rolls back file share backups stored on an immutable short-term repository to a point in time state. | | [Update-VBRNasBackupPath](update-vbrnasbackuppath.md) | Updates the file path to the source file share. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Get-VBRNASBackupFLRItemVersion](get-vbrnasbackupflritemversion.md) | Parameter added: LatestArchivedVersion. | | [Set-VBRFiler](set-vbrfiler.md) | Parameter added: MetaMigrationType. | | [Set-VBRNASBackupJob](set-vbrnasbackupjob.md) | Parameter added: EnableCopyMode. | | [Set-VBRNasFilerNFSServer](set-vbrnasfilernfsserver.md) | Parameters added: BackupIOControlLevel, MetaMigrationType. | | [Set-VBRNasFilerSMBServer](set-vbrnasfilersmbserver.md) | Parameters added: AccessCredentials, BackupIOControlLevel, MetaMigrationType. | | [Set-VBRNASFileServer](set-vbrnasfileserver.md) | Parameter added: CBackupRepository. | | [Set-VBRNASNFSServer](set-vbrnasnfsserver.md) | Parameter added: MetaMigrationType. | | [Set-VBRNASSMBServer](set-vbrnassmbserver.md) | Parameter added: MetaMigrationType. | | [Set-VBRNotificationOptions](set-vbrnotificationoptions.md) | Parameters added: EnableDailyNotification, SendTime. | | [Start-VBRNASBackupHealthCheck](start-vbrnasbackuphealthcheck.md) | Parameters added: Force, CBackupJob. | |

Object Storage Repositories

In Veeam PowerShell v12, cmdlets that apply to object storage repositories were extended and updated.

For more information, see the [Managing Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/managing_object_storage_repo_data.html?ver=13) section in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Get-VBRObjectStorageRepositorySyncInterval](deleted.md) | Returns a time period available for synchronization for checkpoints located in object storage repositories. | | [Get-VBRS3CompatibleRepositorySecurityOptions](get-vbrs3compatiblerepositorysecurityoptions.md) | Returns settings that Veeam Agent uses to access S3 compatible repositories. | | [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) | Defines settings of a mount server used for object storage repositories. | | [Set-VBRRepositoryMountServerOptions](set-vbrrepositorymountserveroptions.md) | Modifies settings of a mount server used for object storage repositories. | | [Set-VBRS3CompatibleRepositorySecurityOptions](set-vbrs3compatiblerepositorysecurityoptions.md) | Modifies settings that Veeam Agent uses to access S3 compatible repositories. | | [Sync-VBRObjectStorageRepositoryEntityState](deleted.md) | Rolls back checkpoints located in object storage repositories to the previous state. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Add-VBRAmazonS3CompatibleRepository](add-vbramazons3compatiblerepository.md) | Parameters added: EnableConcurrentTasksLimit, Force, ForceOwnershipChange, MaxConcurrentTasks, MountServerOptions, ProxyAppliance. | | [Add-VBRAmazonS3GlacierRepository](add-vbramazons3glacierrepository.md) | Parameters added: Force, UseInstantRetrieval. | | [Add-VBRAmazonS3Repository](add-vbramazons3repository.md) | Parameters added: AmazonProxySpec, EnableBackupImmutability, Force, ForceOwnershipChange, MaxConcurrentTasks, MountServerOptions. | | [Add-VBRAzureArchiveRepository](add-vbrazurearchiverepository.md) | Parameters added: EnableBackupImmutability, Force. | | [Add-VBRAzureBlobRepository](add-vbrazureblobrepository.md) | Parameters added: AzureProxySpec, EnableBackupImmutability, EnableConcurrentTasksLimit, EnableCoolAccessTier, Force, ForceOwnershipChange, ImmutabilityPeriod, MaxConcurrentTasks, MountServerOptions. | | [Add-VBRAzureDataBoxRepository](add-vbrazuredataboxrepository.md) | Parameters added: EnableConcurrentTasksLimit, Force, MaxConcurrentTasks. | | [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md) | Parameters added: EnableConcurrentTasksLimit, Force, ForceOwnershipChange, GoogleProxySpec, MaxConcurrentTasks, MountServerOptions | | [Set-VBRAmazonS3CompatibleRepository](set-vbramazons3compatiblerepository.md) | Parameters added: ConnectionType, EnableConcurrentTasksLimit, Force, MaxConcurrentTasks, MountServerOptions, ProxyAppliance | | [Set-VBRAmazonS3GlacierRepository](set-vbramazons3glacierrepository.md) | Parameters added: ConnectionType, Force, UseInstantRetrieval. | | [Set-VBRAmazonS3Repository](set-vbramazons3repository.md) | Parameters added: AmazonProxySpec, ConnectionType, EnableConcurrentTasksLimit, Force, MaxConcurrentTasks, MountServerOptions. | | [Set-VBRAzureArchiveRepository](set-vbrazurearchiverepository.md) | Parameters added: ConnectionType, EnableBackupImmutability, Force, | | [Set-VBRAzureBlobRepository](set-vbrazureblobrepository.md) | Parameters added: AzureProxySpec, ConnectionType, EnableBackupImmutability, EnableConcurrentTasksLimit, EnableCoolAccessTier. | | [Set-VBRAzureDataBoxRepository](set-vbrazuredataboxrepository.md) | Parameters added: ConnectionType, EnableConcurrentTasksLimit, Force, MaxConcurrentTasks. | | [Set-VBRGoogleCloudRepository](set-vbrgooglecloudrepository.md) | Parameters added: ConnectionType, EnableConcurrentTasksLimit, Force, GoogleProxySpec, MaxConcurrentTasks, MountServerOptions. | |

Restore to Microsoft Azure

In Veeam PowerShell v12, cmdlets that apply to restore to Microsoft Azure were extended and updated.

For more information, see the [Restore to Microsoft Azure](https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure.html?ver=13) section in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operation:  | Cmdlet | Operation | | --- | --- | | [New-VBRAzureDiskConfiguration](new-vbrazurediskconfiguration.md) | Defines Azure VM disk types. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Add-VBRAzureAccount](add-vbrazureaccount.md) | Parameters added: ApplicationId, CertificatePath, Description, Name, Password, SecretKey, TenantId, | | [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md) | Parameter added: Location. | | [Get-VBRAzureNetworkSecurityGroup](get-vbrazurenetworksecuritygroup.md) | Parameter added: Location. | | [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) | Parameter added: Location. | | [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) | Parameter added: Location. | | [Set-VBRAzureAccount](set-vbrazureaccount.md) | Parameters added: ApplicationId, CertificatePath, Description, Name, Password, SecretKey, TenantId. | | [Start-VBRVMRestoreToAzure](start-vbrvmrestoretoazure.md) | Parameters added: DiskConfigurations, Location. | |

Scale-Out Backup Repositories

In Veeam PowerShell v12, cmdlets that apply to restore to scale-out backup repositories were extended and updated.

For more information, see the [Rebalancing Extents of Scale-Out Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/sobr_rebalance.html?ver=13) section in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operation:  | Cmdlet | Operation | | --- | --- | | [Start-VBRScaleOutBackupRepositoryRebalance](start-vbrscaleoutbackuprepositoryrebalance.md) | Starts to rebalance data of scale-out backup repositories. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Get-VBRAzureApplianceSession](get-vbrazureappliancesession.md) | Type updated for the Session parameter: changed from the VBRAzureRestoreSession type to VBRAzureApplianceSession type. | | [Set-VBRAzureAccount](set-vbrazureaccount.md) | Parameters added: ApplicationId, CertificatePath, Description, Name, Password, SecretKey, TenantId | |

Storage Systems

In Veeam PowerShell v12, cmdlets that apply to restore to storage systems were extended and updated.

For more information, see the [Adding Cisco HyperFlex](https://helpcenter.veeam.com/docs/vbr/userguide/cisco_add.html?ver=13)  and  [Adding Nutanix Files Storage](https://helpcenter.veeam.com/docs/vbr/userguide/nutanix_add.html?ver=13) sections in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Add-VBRNutanixHost](add-vbrnutanixhost.md) | Adds Nutanix Files storage systems to Veeam Backup & Replication. | | [Get-VBRNutanixHost](get-vbrnutanixhost.md) | Returns Nutanix Files storage systems. | | [Get-VBRNutanixInfrastructureVolume](get-vbrnutanixinfrastructurevolume.md) | Returns Nutanix Files volumes added to the backup infrastructure. | | [Get-VBRNutanixVolume](get-vbrnutanixvolume.md) | Returns all volumes of the specified Nutanix Files storage systems. | | [Remove-VBRNutanixHost](remove-vbrnutanixhost.md) | Removes Nutanix Files storage systems from Veeam Backup & Replication. | | [Set-VBRNutanixHost](set-vbrnutanixhost.md) | Modifies Nutanix Files storage system settings. | | [Sync-VBRNutanixHost](sync-vbrnutanixhost.md) | Rescans Nutanix Files storage systems. | | [Sync-VBRNutanixVolume](sync-vbrnutanixvolume.md) | Rescans Nutanix Files volumes added to the backup infrastructure. | | [Remove-HyperFlexHost](remove-hyperflexhost.md) | Removes Cisco HyperFlex storage systems from the backup infrastructure. | | [Set-HyperFlexHost](set-hyperflexhost.md) | Modifies Cisco HyperFlex storage settings. | | [Sync-HyperFlexHost](sync-hyperflexhost.md) | Rescans Cisco HyperFlex storage system. | |

SureBackup

In Veeam PowerShell v12, cmdlets that apply to SureBackup were extended and updated.

For more information, see the [SureBackup](https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_recovery_verification.html?ver=13) section in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Add-VBRApplicationGroup](add-vbrapplicationgroup.md) | Creates application groups for SureBackup jobs. | | [Add-VBRHvAdvancedVirtualLab](add-vbrhvadvancedvirtuallab.md) | Creates a Hyper-V advanced virtual lab. | | [Add-VBRHvSimpleVirtualLab](add-vbrhvsimplevirtuallab.md) | Creates a Hyper-V basic virtual lab. | | [Add-VBRSureBackupJob](add-vbrsurebackupjob.md) | Creates a SureBackup job. | | [Connect-VBRHvVirtualLab](connect-vbrhvvirtuallab.md) | This cmdlet adds VMs created on Hyper-V to Veeam Backup & Replication. | | [Get-VBRHvVirtualLabConfiguration](get-vbrhvvirtuallabconfiguration.md) | Returns virtual labs and their settings. | | [Get-VBRSureBackupSession](get-vbrsurebackupsession.md) | Returns SureBackup sessions that have been run. | | [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md) | Returns tasks performed during the specified SureBackup session. | | [New-VBRHvIsolatedNetworkOptions](new-vbrhvisolatednetworkoptions.md) | Defines network settings of isolated networks. | | [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md) | Defines production networks options for Hyper-V virtual lab. | | [New-VBRHvVirtualLabProxyAppliance](new-vbrhvvirtuallabproxyappliance.md) | Defines settings of proxy appliances. | | [New-VBRHvVirtualLabStaticIpMappingRule](new-vbrhvvirtuallabstaticipmappingrule.md) | Defines static IP address mapping rules. | | [Set-VBRApplicationGroup](set-vbrapplicationgroup.md) | Modifies settings of application groups. | | [Set-VBRHvisolatednetworkoptions](set-vbrhvisolatednetworkoptions.md) | Modifies network settings of isolated networks for Hyper-V virtual lab. | | [Set-VBRHvNetworkMappingRule](set-vbrhvproductionnetworkoptions.md) | Modifies production network options for Hyper-V virtual lab. | | [Set-VBRHvproductionnetworkoptions](set-vbrhvproductionnetworkoptions.md) | Modifies production network options for Hyper-V virtual lab. | | [Set-VBRHvVirtualLab](set-vbrhvvirtuallab.md) | Modifies settings of Hyper-V virtual labs. | | [Set-VBRHvVirtualLabIPMappingRule](set-vbrhvvirtuallabproxyappliance.md) | Modifies settings of proxy appliances for Hyper-V virtual lab. | | [Set-VBRHvVirtualLabNetworkOptions](set-vbrhvvirtuallabproxyappliance.md) | Modifies settings of proxy appliances for Hyper-V virtual lab. | | [Set-VBRHvVirtualLabProxyAppliance](set-vbrhvvirtuallabproxyappliance.md) | Modifies settings of proxy appliances for Hyper-V virtual lab. | | [Set-VBRHvVirtualLabStaticIpMappingRule](set-vbrhvvirtuallabstaticipmappingrule.md) | Modifies static IP address mapping rules for Hyper-V virtual lab. | | [Set-VBRSureBackupJob](set-vbrsurebackupjob.md) | Modifies settings of SureBackup jobs. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) | Parameters added: EnableEmailNotification, NotifyOnError, NotifyOnSuccess, NotifyOnWarning, Subject, UseCustomEmailSettings. | | [New-VBRSureBackupVM](new-vbrsurebackupvm.md) | Parameter added: RestorePoint. | | [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) | Parameters added: AccessIPv6Address, IsolatedIPv6Address. | | [New-VBRViVirtualLabNetworkOptions](new-vbrvivirtuallabnetworkoptions.md) | Parameters added: EnableDHCPv6, IPv6Address, IPv6DNSServer, IPv6PrefixLength, MasqueradeIPv6Address. | | [New-VBRViVirtualLabProxyAppliance](new-vbrvivirtuallabproxyappliance.md) | Parameters added: SwitchParameter, EnableIPv4Interface, EnableIPv6Interface, IPv6Address, IPv6AlternateDNSServer, IPv6DefaultGateway, IPv6PreferredDNSServer, IPv6PrefixLength, ObtainIPv6AddressAutomatically, ObtainIPv6DNSAutomatically. | | [Set-VBRSureBackupJobVerificationOptions](set-vbrsurebackupjobverificationoptions.md) | Parameters added: NotifyOnError, NotifyOnSuccess, NotifyOnWarning, Subject, UseCustomEmailSettings. | | [Set-VBRViNetworkMappingRule](set-vbrvinetworkmappingrule.md) | Parameter changes:  NetworkMapping changed from non-required to required. | | [Set-VBRViVirtualLabIPMappingRule](set-vbrvivirtuallabipmappingrule.md) | Parameters added: AccessIPv6Address, IsolatedIPv6Address, | | [Set-VBRViVirtualLabNetworkOptions](set-vbrvivirtuallabnetworkoptions.md) | Parameters added: EnableDHCPv6, IPv6Address, IPv6DNSServer, IPv6PrefixLength, MasqueradeIPv6Address, | | [Set-VBRViVirtualLabProxyAppliance](set-vbrvivirtuallabproxyappliance.md) | Parameters added: EnableIPv4Interface, EnableIPv6Interface, IPv6Address, IPv6AlternateDNSServer, IPv6DefaultGateway, IPv6PreferredDNSServer, IPv6PrefixLength, ObtainIPv6AddressAutomatically, ObtainIPv6DNSAutomatically. | |

Tapes

In Veeam PowerShell v12, cmdlets that apply to tape devices support were extended and updated.

For more information, see the [Tape Devices Support](https://helpcenter.veeam.com/docs/vbr/userguide/tape_device_support.html?ver=13) section in the Veeam User Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) | Looks for files or folders backed-up by tape jobs. | | [Find-VBRTapeCatalogItemVersion](find-vbrtapecatalogitemversion.md) | Looks for backed up versions of a file or folder. | | [Get-VBRTapeBackupSession](get-vbrtapebackupsession.md) | Returns tape backup job sessions. | | [Start-VBRTapeFileRestore](start-vbrtapefilerestore.md) | Starts the restore of files and folders from tape. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [Add-VBRBackupToTapeJob](add-vbrbackuptotapejob.md) | Parameter added: PreventInterruption. | | [Add-VBRFileToTapeJob](add-vbrfiletotapejob.md) | Parameters added: EnableFileAclChangeTracking, EnableParallelDrivesUsage, LimitTapeDrives. | | [Add-VBRTapeServer](add-vbrtapeserver.md) | Parameter added: Force. | | [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md) | Cmdlet set changes: The Path parameter added to the cmdlet set that deines shared folders as a source for file to tape jobs. | | [Remove-VBRTapeMedium](remove-vbrtapemedium.md) | Parameter added: FromVault. | | [Set-VBRBackupToTapeJob](set-vbrbackuptotapejob.md) | Parameter added: PreventInterruption. | | [Set-VBRFileToTapeJob](set-vbrfiletotapejob.md) | Parameters added: EnableFileAclChangeTracking, EnableParallelDrivesUsage, LimitTapeDrives | | [Set-VBRTapeMediaPool](set-vbrtapemediapool.md) | Parameter added: Medium. | |

Veeam Agent Management

In Veeam PowerShell v12, cmdlets that apply to Veeam Agent management were extended and updated.

For more information, see the [Veeam Agent Management Guide](https://helpcenter.veeam.com/docs/backup/agents/introduction.html?ver=120).

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform operations with tokens, file proxy servers and modify a protection scope of Azure and Amazon objects.  | Cmdlet | Operation | | --- | --- | | [Add-VBRComputerRecoveryToken](add-vbrcomputerrecoverytoken.md) | Creates tokens for bare-metal recovery | | [Disable-VBRComputerFileProxyServer](disable-vbrcomputerfileproxyserver.md) | Disables file proxy servers. | | [Enable-VBRComputerFileProxyServer](enable-vbrcomputerfileproxyserver.md) | Enables disabled file proxy servers. | | [Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md) | Returns tokens for bare-metal recovery. | | [New-VBRAmazonEC2Container](new-vbramazonec2container.md) | Defines a scope of Amazon EC2 instances, EC2 tags or AWS datacenters for a protection group. | | [New-VBRAzureContainer](new-vbrazurecontainer.md) | Defines a scope of Azure VMs, Azure tags or Azure Availability Zone for a protection group. | | [Remove-VBRComputerRecoveryToken](remove-vbrcomputerrecoverytoken.md) | Removes tokens for bare-metal recovery. | | [Set-VBRAmazonEC2Container](set-vbramazonec2container.md) | Modifies a scope of Amazon EC2 instances, EC2 tags or AWS datacenters for a protection group. | | [Set-VBRAzureContainer](set-vbrazurecontainer.md) | Modifies a scope of Azure VMs, Azure tags or Azure Availability Zone for a protection group. | | [Set-VBRComputerRecoveryToken](set-vbrcomputerrecoverytoken.md) | Modifies tokens for bare-metal recovery. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| In Veeam Backup & Replication v12, the following cmdlets were updated:  | Cmdlet | Operation | | --- | --- | | [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) | Parameter added: ReadEntireRestorePoint | | [New-VBRPostgreSQLProcessingOptions](new-vbrpostgresqlprocessingoptions.md) | Parameters added: ArchiveLogBackupPeriod, ArchiveLogBackupStorage. | | [New-VBRProtectionGroupDeploymentOptions](new-vbrprotectiongroupdeploymentoptions.md) | Parameter added: ReadEntireRestorePoint. | | [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) | Type updated for the HealthCheckOptions parameter: changed from the VBRFullBackupOptions type to VBRHealthCheckOptions type. | | [Set-VBRComputerGFSOptions](set-vbrcomputergfsoptions.md) | Parameter added: ReadEntireRestorePoint. | | [Set-VBRLinuxSelectedVolume](set-vbrlinuxselectedvolume.md) | Parameter updated: SelectedVolume accepts pipeline input: True(ByValue). | | [Set-VBRPostgreSQLProcessingOptions](set-vbrpostgresqlprocessingoptions.md) | Parameters added: ArchiveLogBackupPeriod, ArchiveLogBackupStorage. | | [Set-VBRSanIntegrationOptions](set-vbrsanintegrationoptions.md) | Parameter updated: SanIntegrationOptions accept pipeline input: True(ByValue). | |

Veeam Plug-in Management

In Veeam PowerShell v12, cmdlets that apply to Veeam Plug-in management were delivered.

For more information, see [Veeam Plug-in Management](https://helpcenter.veeam.com/docs/backup/plugins/management.html?ver=120) section of the Veeam Plug-ins for Enterprise Applications Guide.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Starting from v12, you can perform the following operations:  | Cmdlet | Operation | | --- | --- | | [Add-VBRApplicationBackupJob](add-vbrapplicationbackupjob.md) | Creates application backup policies. | | [Disable-VBRApplicationBackupJob](disable-vbrapplicationbackupjob.md) | Disables application backup policies. | | [Enable-VBRApplicationBackupJob](enable-vbrapplicationbackupjob.md) | Enables application backup policies. | | [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) | Returns application backup policies. | | [Get-VBRApplicationBackupJobSession](get-vbrapplicationbackupjobsession.md) | Returns jobs sessions. | | [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) | Returns discovered applications from the computer. | | [Get-VBRPluginBackupSession](get-vbrpluginbackupsession.md) | Returns application backup policy sessions. | | [Get-VBRPluginRestoreSession](get-vbrpluginrestoresession.md) | Returns active restore sessions of application policies. | | [Install-VBRDiscoveredComputerPlugin](install-vbrdiscoveredcomputerplugin.md) | Installs Veeam Plug-Ins on discovered computers. | | [New-VBRApplicationBackupOptions](new-vbrapplicationbackupoptions.md) | Creates the backup settings and full backup schedule for application backup policies. | | [New-VBRApplicationScheduleOptions](new-vbrapplicationscheduleoptions.md) | Creates the schedule for application backup policies. | | [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md) | Creates the database processing settings for application backup policies. | | [New-VBROracleRMANOptions](new-vbroraclermanoptions.md) | Creates the Oracle RMAN backup settings for application backup policies. | | [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md) | Creates the Oracle RMAN database processing settings for application backup policies. | | [New-VBROracleRMANStorageOptions](new-vbroraclermanstorageoptions.md) | Creates the Oracle RMAN storage settings for application backup policies. | | [New-VBRSAPHANACredentialsOptions](new-vbrsaphanacredentialsoptions.md) | Creates the SAP HANA credentials settings for application backup policies. | | [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md) | Creates the SAP HANA backup settings for application backup policies. | | [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md) | Creates the SAP HANA database processing settings for application backup policies. | | [New-VBRSAPOnOracleOptions](new-vbrsaponoracleoptions.md) | Creates the SAP on Oracle backup settings for application backup policies. | | [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md) | Creates the SAP on Oracle database processing settings for application backup policies. | | [New-VBRSAPOnOracleStorageOptions](new-vbrsaponoraclestorageoptions.md) | Creates the SAP on Oracle storage settings for application backup policies. | | [Remove-VBRApplicationBackupJob](remove-vbrapplicationbackupjob.md) | Removes application backup policies. | | [Reset-VBRPluginCertificate](reset-vbrplugincertificate.md) | Resets Veeam Plug-In SSL certificates. | | [Set-VBRApplicationBackupJob](set-vbrapplicationbackupjob.md) | Modifies application backup policies. | | [Set-VBRDatabaseProcessingOptions](set-vbrdatabaseprocessingoptions.md) | Modifies the database processing settings for application backup policies. | | [Set-VBROracleRMANProcessingOptions](set-vbroraclermanprocessingoptions.md) | Modifies the Oracle RMAN database processing settings for application backup policies. | | [Set-VBRSAPHANAProcessingOptions](set-vbrsaphanaprocessingoptions.md) | Modifies the SAP HANA database processing settings for application backup policies. | | [Set-VBRSAPOnOracleProcessingOptions](set-vbrsaponoracleprocessingoptions.md) | Modifies the SAP on Oracle database processing settings for application backup policies. | | [Start-VBRApplicationBackupJob](start-vbrapplicationbackupjob.md) | Starts application backup policies. | | [Stop-VBRApplicationBackupJob](stop-vbrapplicationbackupjob.md) | Stops application backup policies. | | [Uninstall-VBRDiscoveredComputerPlugin](uninstall-vbrdiscoveredcomputerplugin.md) | Removes Veeam Plug-In from a specific protected computer. | |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
