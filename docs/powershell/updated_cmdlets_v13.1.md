---
title: "Updated Cmdlets"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/updated_cmdlets_v13.1.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Updated Cmdlets


This section contains information on cmdlets updated in Veeam PowerShell v13.1.

Backup Infrastructure

NetApp NDMP Storage

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Get-VBRNDMPVolume](get-vbrndmpvolume.md) | Type updated for the Server parameter: changed from the VBRNDMPServer[] type to the VBRNDMPServerBase[] type. | | [Remove-VBRNDMPServer](remove-vbrndmpserver.md) | Type updated for the Server parameter: changed from the VBRNDMPServer[] type to the VBRNDMPServerBase[] type. | | [Add-NetAppHost](add-netapphost.md) | New parameter: EnableNDMPBackup. | | [Set-NetAppHost](set-netapphost.md) | New parameter: EnableNDMPBackup. | |

Backup

Tape — Database Plugin Backups

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Start-VBRTapeRestore](start-vbrtaperestore.md) | New parameter: DbPluginRestorePoint. | |

Microsoft Entra ID Support

Microsoft Entra ID Tenant Backup

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBREntraIDTenantBackupJob](add-vbrentraidtenantbackupjob.md) | New parameter: TargetBackup. | | [Set-VBREntraIDTenantBackupJob](set-vbrentraidtenantbackupjob.md) | New parameters: EnableSecondaryTarget, TargetBackup. | |

Backup Infrastructure

Roles and Access Control

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRUserRoleAssignment](add-vbruserroleassignment.md) | New parameter: RoleEntity. | | [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) | New parameter: RoleEntity. | | [Set-VBRUserRoleAssignment](set-vbruserroleassignment.md) | New parameter: RoleEntity. | |

Veeam Agent Management

Discovered Computers

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRDiscoveredComputerRecoveryMedia](add-vbrdiscoveredcomputerrecoverymedia.md) | New parameter: EnableRemoteBmr. | |

Data Recovery

Unstructured Data — Cold Storage Retrieval

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Copy-VBRUnstructuredBackup](copy-vbrunstructuredbackup.md) | New parameters: Force, RetrievalSettings. | | [Restore-VBRUnstructuredBackupFLRItem](restore-vbrunstructuredbackupflritem.md) | New parameters: Force, RetrievalSettings. | | [Save-VBREntraIDLogsBackupFLRItem](save-vbrentraidlogsbackupflritem.md) | New parameters: Force, RetrievalSettings. | | [Save-VBRUnstructuredBackupFLRItem](save-vbrunstructuredbackupflritem.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRAmazonS3Server](set-vbramazons3server.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRAzureStorageServer](set-vbrazurestorageserver.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRFiler](set-vbrfiler.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRNASFileServer](set-vbrnasfileserver.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRNASNFSServer](set-vbrnasnfsserver.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRNASSMBServer](set-vbrnassmbserver.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRNasFilerNFSServer](set-vbrnasfilernfsserver.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRNasFilerSMBServer](set-vbrnasfilersmbserver.md) | New parameters: Force, RetrievalSettings. | | [Set-VBRS3CompatibleServer](set-vbrs3compatibleserver.md) | New parameter: RetrievalSettings. | | [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) | New parameters: Force, RetrievalSettings. | | [Start-VBRNasBackupRestore](start-vbrnasbackuprestore.md) | New parameters: Force, RetrievalSettings. | | [Start-VBRObjectStorageBackupRestore](start-vbrobjectstoragebackuprestore.md) | New parameters: Force, RetrievalSettings. | | [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) | New parameters: Force, RetrievalSettings. | | [Start-VBRUnstructuredBackupHealthCheck](start-vbrunstructuredbackuphealthcheck.md) | New parameters: EnableColdStorageRetrieval, RetrievalSettings. | | [Sync-VBRUnstructuredBackupMetadata](sync-vbrunstructuredbackupmetadata.md) | New parameters: Force, RetrievalSettings. | | [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) | New parameter: GfsPolicyOptions. | | [Set-VBRUnstructuredBackupSecondaryTarget](set-vbrunstructuredbackupsecondarytarget.md) | New parameter: GfsPolicyOptions. | |

Malware Detection

Encrypted Data and Unstructured Backup Scans

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRMalwareDetectionExclusion](add-vbrmalwaredetectionexclusion.md) | New parameters: AutoScanDisabled, ExcludeEntireObject, ExcludedActivities, ExcludedPaths. | | [Get-VBRMalwareDetectionExclusion](get-vbrmalwaredetectionexclusion.md) | New parameters: AutoScanDisabled, Entity, ExcludeEntireObject, ExcludedActivities, ExcludedPaths, Id, Name, Note, Platform. | | [Set-VBRMalwareDetectionExclusion](set-vbrmalwaredetectionexclusion.md) | New parameters: AutoScanDisabled, ExcludeEntireObject, ExcludedActivities, ExcludedPaths. | | [Remove-VBRMalwareDetectionExclusion](remove-vbrmalwaredetectionexclusion.md) | Type updated for the Exclusion parameter: changed from the VBRMalwareDetectionExclusion[] type to the VBRMalwareDetectionExclusion type.  The Exclusion parameter changed from position 0 to named. | |

Backup Infrastructure

High Availability (HA) Cluster

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRHighAvailabilityCluster](add-vbrhighavailabilitycluster.md) | New parameters: PrimaryNodeExternalEndpoint, PrimaryNodeIPAddress, SecondaryNodeExternalEndpoint.  Parameter removed: PrimaryNodeHostName. | | [New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md) | New parameter: SecondaryNodeIPAddress.  Parameter removed: HostName. | |

Backup

Backup Termination Window

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [New-VBRUnixScheduleOptions](new-vbrunixscheduleoptions.md) | New parameters: EnableBackupTerminationWindow, TerminationWindow. | | [New-VBRLinuxScheduleOptions](new-vbrlinuxscheduleoptions.md) | New parameters: EnableBackupTerminationWindow, TerminationWindow. | | [Set-VBRLinuxScheduleOptions](set-vbrlinuxscheduleoptions.md) | New parameters: EnableBackupTerminationWindow, TerminationWindow. | | [New-VBRMacScheduleOptions](new-vbrmacscheduleoptions.md) | New parameters: EnableBackupTerminationWindow, TerminationWindow. | | [Set-VBRMacScheduleOptions](set-vbrmacscheduleoptions.md) | New parameters: EnableBackupTerminationWindow, TerminationWindow. | |

Backup Infrastructure

Hosts and Storage Systems Cleanup

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Remove-HP3Storage](remove-hp3storage.md) | New parameters: CleanupHost, Force. | | [Remove-HyperFlexHost](remove-hyperflexhost.md) | New parameters: CleanupHost, Force. | | [Remove-NetAppHost](remove-netapphost.md) | New parameters: CleanupHost, Force. | | [Remove-NimbleHost](remove-nimblehost.md) | New parameters: CleanupHost, Force. | | [Remove-StoragePluginHost](remove-storagepluginhost.md) | New parameters: CleanupHost, Force. | | [Remove-ThinkSystemHost](remove-thinksystemhost.md) | New parameters: CleanupHost, Force. | | [Remove-VBRIsilonHost](remove-vbrisilonhost.md) | New parameters: CleanupHost, Force. | | [Remove-VBRNutanixHost](remove-vbrnutanixhost.md) | New parameters: CleanupHost, Force. | | [Remove-VNXHost](remove-vnxhost.md) | New parameters: CleanupHost, Force. | |

Storage Plug-ins — Application-Aware Backup

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-StoragePluginHost](add-storagepluginhost.md) | New parameters: ApplicationFC, ApplicationISCSI, EnableApplicationBackup. | | [Set-StoragePluginHost](set-storagepluginhost.md) | New parameters: ApplicationExcludedVolume, ApplicationExcludedWildcard, ApplicationIncludedVolume, ApplicationIncludedWildcard, ApplicationProtocolPolicy, ApplicationVolumeScanType, EnableApplicationBackup. | |

Data Recovery

Instant Recovery and Guest File Restore

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Restart-VBRInstantRecovery](restart-vbrinstantrecovery.md) | New parameter: ForceArchivedSnapshotsRestore. | | [Start-VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md) | New parameter: SkipNetworkSecurityGroup. | | [Start-VBRInstantRecovery](start-vbrinstantrecovery.md) | New parameters: EnableClusterWideMount, ForceArchivedSnapshotsRestore. | | [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) | New parameter: ForceArchivedSnapshotsRestore. | | [Start-VBRLinuxGuestItemRestore](start-vbrlinuxguestitemrestore.md) | New parameter: ForceArchivedSnapshotsRestore. | | [Start-VBRVMRestoreToAzure](start-vbrvmrestoretoazure.md) | New parameter: SkipNetworkSecurityGroup. | | [Start-VBRViComputerInstantRecovery](start-vbrvicomputerinstantrecovery.md) | New parameter: EnableClusterWideMount. | | [Start-VBRViInstantVMDiskRecovery](start-vbrviinstantvmdiskrecovery.md) | New parameters: EnableClusterWideMount, ForceArchivedSnapshotsRestore. | | [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) | New parameter: ForceArchivedSnapshotsRestore. | | [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) | New parameter: ForceArchivedSnapshotsRestore. | |

NDMP Volume Restore

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Start-VBRNDMPVolumeRestore](start-vbrndmpvolumerestore.md) | New parameter: EnableVolumeWriteAccess.  Type updated for the Server parameter: changed from the VBRNDMPServer type to the VBRNDMPServerBase type. | |

Disk Publishing (Data Integration API)

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Publish-VBRBackupContent](publish-vbrbackupcontent.md) | New parameters: Folder, ResourcePool, StorageHost. | |

Repository Extent Backup Evacuation

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Start-VBRRepositoryExtentBackupEvacuation](start-vbrrepositoryextentbackupevacuation.md) | Type updated for the Extent parameter: changed from the VBRRepositoryExtent[] type to the IVBRExtent[] type. | |

Backup Infrastructure

Object Storage Repositories — Immutability

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBR1111SystemsS3Repository](add-vbr1111systemss3repository.md) | New parameter: EnableReadOnlyMode. | | [Add-VBRAmazonS3CompatibleRepository](add-vbramazons3compatiblerepository.md) | New parameter: EnableReadOnlyMode. | | [Add-VBRAmazonS3GlacierRepository](add-vbramazons3glacierrepository.md) | New parameters: EnableReadOnlyMode, ImmutabilityMode, ImmutabilityPeriod. | | [Add-VBRAmazonS3Repository](add-vbramazons3repository.md) | New parameter: EnableReadOnlyMode. | | [Add-VBRAzureArchiveRepository](add-vbrazurearchiverepository.md) | New parameters: EnableReadOnlyMode, ImmutabilityMode, ImmutabilityPeriod. | | [Add-VBRAzureBlobRepository](add-vbrazureblobrepository.md) | New parameter: EnableReadOnlyMode. | | [Add-VBRDataCloudVaultRepository](add-vbrdatacloudvaultrepository.md) | New parameter: EnableReadOnlyMode. | | [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md) | New parameter: EnableReadOnlyMode. | | [Add-VBRIBMCloudRepository](add-vbribmcloudrepository.md) | New parameter: EnableReadOnlyMode. | | [Add-VBRS3GlacierCompatibleRepository](add-vbrs3glaciercompatiblerepository.md) | New parameters: EnableReadOnlyMode, ImmutabilityMode, ImmutabilityPeriod. | | [Set-VBRAmazonS3GlacierRepository](set-vbramazons3glacierrepository.md) | New parameters: ImmutabilityMode, ImmutabilityPeriod. | | [Set-VBRAzureArchiveRepository](set-vbrazurearchiverepository.md) | New parameters: ImmutabilityMode, ImmutabilityPeriod. | | [Set-VBRS3GlacierCompatibleRepository](set-vbrs3glaciercompatiblerepository.md) | New parameters: ImmutabilityMode, ImmutabilityPeriod. | |

Backup Repository

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Set-VBRBackupRepository](set-vbrbackuprepository.md) | New parameter: StoreOnceWanLink. | | [Add-VBRScaleOutBackupRepository](add-vbrscaleoutbackuprepository.md) | New parameters: EnableArchiveTierCopyPolicy, EnableArchiveTierMovePolicy. | | [Set-VBRScaleOutBackupRepository](set-vbrscaleoutbackuprepository.md) | New parameters: EnableArchiveTierCopyPolicy, EnableArchiveTierMovePolicy. | |

Backup Server Certificates

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRBackupServerCertificate](add-vbrbackupservercertificate.md) | New parameter: Force. | | [Generate-VBRBackupServerDeployerKit](generate-vbrbackupserverdeployerkit.md) | Now also generates installation packages for Unix computers, in addition to Microsoft Windows and Linux. | | [Remove-VBRBackupServerDeployerCertificate](remove-vbrbackupserverdeployercertificate.md) | Now removes all Veeam Deployer Service certificates from the database in a single operation. | |

Backup Copy

Backup Copy Job — Target Repository

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) | Parameter removed: TargetBackup. | | [Add-VBREntraIDLogsBackupJob](add-vbrentraidlogsbackupjob.md) | Parameter removed: TargetBackup. | | [Add-VBRHvBackupJob](add-vbrhvbackupjob.md) | Parameter removed: TargetBackup. | | [Add-VBRViBackupJob](add-vbrvibackupjob.md) | Parameter removed: TargetBackup. | | [Add-VBRvCloudJob](add-vbrvcloudjob.md) | Parameter removed: TargetBackup. | | [Set-VBRBackupCopyJob](set-vbrbackupcopyjob.md) | Parameter removed: TargetBackup. | | [Set-VBREntraIDLogsBackupJob](set-vbrentraidlogsbackupjob.md) | Parameter removed: TargetBackup. | |

Backup Infrastructure

Veeam Cloud Connect Cloud Providers

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRCloudProvider](add-vbrcloudprovider.md) | New parameter: RestoreAccessLevel. | | [Set-VBRCloudProvider](set-vbrcloudprovider.md) | New parameter: RestoreAccessLevel. | |

Backup

Protection Groups

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) | New parameter: CacheRepository. | | [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) | New parameter: CacheRepository. | | [New-VBRProtectionGroupAdvancedWindowsOptions](new-vbrprotectiongroupadvancedwindowsoptions.md) | New parameter: CreateEmbeddedRecoveryMedia. | | [New-VBRProtectionGroupDeploymentOptions](new-vbrprotectiongroupdeploymentoptions.md) | New parameter: InstallNoSnapAgent. | |

SureBackup Content Scan Jobs

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRSureBackupContentScanJob](add-vbrsurebackupcontentscanjob.md) | New parameter: UnstructuredLinkedJob.  The LinkedJob parameter is no longer required. | | [Set-VBRSureBackupContentScanJob](set-vbrsurebackupcontentscanjob.md) | New parameter: UnstructuredLinkedJob. | |

Data Replication

Universal CDP Policy

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRUniversalCDPPolicy](add-vbruniversalcdppolicy.md) | New parameters: GuestProcessingOptions, OriginalMachine, ReIpRule, ReplicaMachine, RepositorySeed. | | [Set-VBRUniversalCDPPolicy](set-vbruniversalcdppolicy.md) | New parameters: EnableGuestProcessing, EnableReplicaMapping, EnableReplicaSeeding, GuestProcessingOptions, OriginalMachine, ReIpRule, ReplicaMachine, RepositorySeed. | |

Backup Infrastructure

Azure Restore Proxy

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRAzureRestoreProxy](add-vbrazurerestoreproxy.md) | New parameters: NetworkSecurityGroup, SkipNetworkSecurityGroup. | |

Application Backup Policies

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRApplicationBackupJob](add-vbrapplicationbackupjob.md) | New parameter: GFSOptions. | | [Set-VBRApplicationBackupJob](set-vbrapplicationbackupjob.md) | New parameter: GFSOptions. | |

NAS Backup Job

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRNASBackupJob](add-vbrnasbackupjob.md) | New parameter: IncludeSymbolicLinkContent. | | [Set-VBRNASBackupJob](set-vbrnasbackupjob.md) | New parameter: IncludeSymbolicLinkContent. | |

Data Recovery

Mail Notifications

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Set-VBRMailNotificationConfiguration](set-vbrmailnotificationconfiguration.md) | New parameter: AIGenerated. | |

Backup Infrastructure

Veeam Plug-ins for Enterprise Applications — SAP HANA and SQL Processing

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md) | New parameters: Prefix, UseCustomPrefix. | | [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md) | New parameter: UseSqlAuthentication. | | [Set-VBRSQLProcessingOptions](set-vbrsqlprocessingoptions.md) | New parameter: UseSqlAuthentication. | |

Active Directory Container Credentials

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [New-VBRADContainer](new-vbradcontainer.md) | New parameter: UseTemporaryCertificate. | | [New-VBRADCustomCredentials](new-vbradcustomcredentials.md) | New parameter: UseTemporaryCertificate.  The Credentials parameter is now required. | | [Set-VBRADContainer](set-vbradcontainer.md) | New parameter: UseTemporaryCertificate. | |

Catalyst Copy Jobs

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Add-VBRCatalystCopyJob](add-vbrcatalystcopyjob.md) | Parameters removed: BackupWindowOptions, Description, EnableHealthCheck, Force, KeepSecondaryCopies, Name, NotificationOptions, ScriptOptions, SecondaryCopiesRetentionPeriod, SourceRepository, TargetRepository. | | [Disable-VBRCatalystCopyJob](disable-vbrcatalystcopyjob.md) | Parameters removed: Confirm, Job, PassThru, WhatIf. | | [Enable-VBRCatalystCopyJob](enable-vbrcatalystcopyjob.md) | Parameters removed: Job, PassThru. | | [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) | Parameters removed: Id, Name. | | [Remove-VBRCatalystCopyJob](remove-vbrcatalystcopyjob.md) | Parameters removed: Confirm, Job, WhatIf. | | [Set-VBRCatalystCopyJob](set-vbrcatalystcopyjob.md) | Parameters removed: AnyTime, BackupWindowOptions, Description, EnableHealthCheck, Force, Job, KeepSecondaryCopies, Name, NotificationOptions, ScriptOptions, SecondaryCopiesRetentionPeriod, SourceRepository, TargetRepository. | | [Start-VBRCatalystCopyJob](start-vbrcatalystcopyjob.md) | Parameter removed: Job. | |

Backup

Working with Jobs

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Get-VBRBackupSession](get-vbrbackupsession.md) | New parameter: State.  The Id parameter is now required. | | [Start-VBRJob](start-vbrjob.md) | New parameter: Force. | |

Discovered Applications

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) | New parameters: Iris, IrisEntityType. | |

Removed Cmdlets

The following cmdlet was removed in Veeam PowerShell v13.1.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Removed Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Removed Cmdlets  | Cmdlet | Operation | | Get-VBRBackupServerDeployerCertificate | Removed. Previously downloaded Veeam Installer Service and Veeam Deployer Service certificates. | |

Page updated 2026-07-29

