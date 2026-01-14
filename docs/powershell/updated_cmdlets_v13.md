---
title: "Updated Cmdlets"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/updated_cmdlets_v13.html"
last_updated: "9/8/2025"
product_version: "13.0.1.1071"
---

# Updated Cmdlets

In this article

This section contains information on cmdlets updated in Veeam PowerShell v13.

Getting Started

In this version, you can view all cmdlets delivered in Veeam PowerShell v13.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRCommand](get-vbrcommand.md) | New parameters: V130. | |

Connecting to Veeam Backup Server

In this version, you can force the TLS certificate of the backup server to be accepted when you connect to a local or remote Veeam backup server.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Connect-VBRServer](connect-vbrserver.md) | New parameters: ForceAcceptTlsCertificate. | |

Managing Security Settings

This section describes changes of Veeam Backup & Replication security settings.

Malware Detection

In version, you can do the following:

* Set Veeam Threat Hunter to start automatically after creating the Suspicious malware detection event.
* Set malware detection events to be automatically marked as clean when a proactive or signature-based scan detects no threats
* Specify a restore point to scan.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Set-VBRMalwareDetectionOptions](set-vbrmalwaredetectionoptions.md) | New parameters: StartThreatHunterAfterDetection, AutoResolveEventAfterCleanScan. | | [Start-VBRScanBackup](start-vbrscanbackup.md) | New parameter: RestorePoint. | |

Backup Infrastructure

Virtualization Servers and Hosts

In this version, you can add servers and hosts using certificate-based authentication.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRLinux](add-vbrlinux.md) | New parameters: UseCertificate, SSHFingerprint, Package, HandshakeCode. | | [Set-VBRLinux](set-vbrlinux.md) | New parameters: UseCertificate, SSHFingerprint, Package, HandshakeCode. | | [Add-VBRHvHost](add-vbrhvhost.md) | New parameters: UseCertificate. | | [Add-VBRWinServe](add-vbrwinserver.md) | New parameters: UseCertificate. | | [Set-VBRHvHost](set-vbrhvhost.md) | New parameters: UseCertificate. | | [Set-VBRWinServer](set-vbrwinserver.md) | New parameters: UseCertificate. | |

Backup Repositories

In this version, you can specify mount server settings for external repositories.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRAmazonS3ExternalRepository](add-vbramazons3externalrepository.md) | New parameters: MountServerOptions, EnableVPowerNFS. | | [Add-VBRAzureExternalRepository](add-vbrazureexternalrepository.md) | New parameters: MountServerOptions, EnableVPowerNFS. | |

Object Storage Repositories

In this version, you can set the type of the immutability period to depend on the backup job retention or on the minimum immutability period.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBR1111SystemsS3Repository](add-vbr1111systemss3repository.md) | New parameter: ImmutabilityMode. | | [Set-VBR1111SystemsS3Repository](set-vbr1111systemss3repository.md) | New parameter: ImmutabilityMode. | | [Add-VBRAmazonS3CompatibleRepository](add-vbramazons3compatiblerepository.md) | New parameter: ImmutabilityMode. | | [Set-VBRAmazonS3CompatibleRepository](set-vbramazons3compatiblerepository.md) | New parameter: ImmutabilityMode. | | [Add-VBRAmazonS3Repository](add-vbramazons3repository.md) | New parameter: ImmutabilityMode. | | [Set-VBRAmazonS3Repository](set-vbramazons3repository.md) | New parameter: ImmutabilityMode. | | [Add-VBRAzureBlobRepository](add-vbrazureblobrepository.md) | New parameter: ImmutabilityMode. | | [Set-VBRAzureBlobRepository](set-vbrazureblobrepository.md) | New parameter: ImmutabilityMode. | | [Add-VBRDataCloudVaultRepository](add-vbrdatacloudvaultrepository.md) | New parameter: ImmutabilityMode. | | [Set-VBRDataCloudVaultRepository](set-vbrdatacloudvaultrepository.md) | New parameter: ImmutabilityMode. | | [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md) | New parameters: ImmutabilityPeriod, ImmutabilityMode, EnableBackupImmutability, ImmutabilityMode. | | [Set-VBRGoogleCloudRepository](set-vbrgooglecloudrepository.md) | New parameters: ImmutabilityPeriod, ImmutabilityMode, EnableBackupImmutability, ImmutabilityMode. | | [Add-VBRIBMCloudRepository](add-vbribmcloudrepository.md) | New parameter: ImmutabilityMode. | | [Set-VBRIBMCloudRepository](set-vbribmcloudrepository.md) | New parameter: ImmutabilityMode. | |

External Repositories

In this version, you can specify mount server settings for external repositories.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRAmazonS3ExternalRepository](add-vbramazons3externalrepository.md) | New parameter: MountServerOptions. | | [Add-VBRAzureExternalRepository](add-vbrazureexternalrepository.md) | New parameter: MountServerOptions. | | [Add-VBRGoogleCloudExternalRepository](add-vbrgooglecloudexternalrepository.md) | New parameter: MountServerOptions. | | [Set-VBRAmazonS3ExternalRepository](set-vbramazons3externalrepository.md) | New parameter: MountServerOptions. | | [Set-VBRAzureExternalRepository](set-vbrazureexternalrepository.md) | New parameter: MountServerOptions. | | [Set-VBRGoogleCloudExternalRepository](set-vbrgooglecloudexternalrepository.md) | New parameter: MountServerOptions. | |

Logging

In this version, you can collect logs from the scale-out backup repository.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Export-VBRLogs](export-vbrlogs.md) | New parameter: ScaleOutRepository . | |

Network Traffic Management

In this version, you can enable throttling for restore operations.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Set-VBRNetworkTrafficRule](set-vbrnetworktrafficrule.md) | New parameter: AllowRestoreThrottling. | | [Add-VBRNetworkTrafficRule](add-vbrnetworktrafficrule.md) | New parameter: AllowRestoreThrottling. | |

Data Recovery

Restore to Amazon EC2

In version, you can specify a dynamic or static private IP address that will be assigned to the restored workload.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRVMRestoreToAmazon](start-vbrvmrestoretoamazon.md) | New parameter: PrivateIpAddress. | |

Guest OS File Recovery

In version, you can do the following:

* Specify the ID of an isolated network.
* Specify configuration settings for a temporary helper appliance.
* Specify the mount server to which you want to mount machine disks.
* Specify the credentials that you want to use to access the shared folder.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRFileRestoreLinuxHelperApplianceOptions](new-vbrfilerestorelinuxhelperapplianceoptions.md) | New parameter: VLanId. | | [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) | New parameter: ApplianceOptions. | | [Start-VBRCDPWindowsFileRestore](start-vbrcdpwindowsfilerestore.md) | New parameter: MountHost. | | [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) | New parameter: ShareCredentials. | |

Microsoft EntraID Support

In this version, you can specify the secondary repository settings for Microsoft Entra ID tenant backup jobs, and the restore reason for the Microsoft Entra ID items.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBREntraIDTenantBackupJob](add-vbrentraidtenantbackupjob.md) | New parameter: SecondaryTarget. | | [Set-VBREntraIDTenantBackupJob](set-vbrentraidtenantbackupjob.md) | New parameter: SecondaryTarget. | | [Restore-VBREntraIDTenantItem](restore-vbrentraidtenantitem.md) | New parameter: Reason. | | [Restore-VBREntraIDTenantItemAttributes](restore-vbrentraidtenantitemattributes.md) | New parameter: Reason. | |

Storage Systems

In this version, you can specify an array of mount hosts and the NVMe protocol for Storage Systems.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VNXHost](add-vnxhost.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Set-VNXHost](set-vnxhost.md) | New parameters: WindowsMountServer, LinuxMountServer. | | [Add-HP3Storage](add-hp3storage.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Set-HP3Storage](set-hp3storage.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Add-NimbleHost](add-nimblehost.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Set-NimbleHost](set-nimblehost.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Add-ThinkSystemHost](add-thinksystemhost.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Set-ThinkSystemHost](set-thinksystemhost.md) | New parameters: WindowsMountServer, LinuxMountServer. | | [Add-NetAppHost](add-netapphost.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Set-NetAppHost](set-netapphost.md) | New parameters: WindowsMountServer, LinuxMountServer. | | [Add-StoragePluginHost](add-storagepluginhost.md) | New parameters: WindowsMountServer, LinuxMountServer, NVMe. | | [Set-StoragePluginHost](set-storagepluginhost.md) | New parameters: WindowsMountServer, LinuxMountServer. | | [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) | New parameter: NVMe. | |

Tape Devices

In this version, you can specify settings for GFS file to tape jobs.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRFileToTapeJob](add-vbrfiletotapejob.md) | New parameters: GFSScheduleOptions, GFSMediaSetsToExport, GFSMediaPool. | | [Set-VBRFileToTapeJob](set-vbrfiletotapejob.md) | New parameters: GFSScheduleOptions, GFSMediaSetsToExport, GFSMediaPool. | | [Set-VBRObjectToTapeJob](set-vbrobjecttotapejob.md) | New parameters: GFSScheduleOptions, GFSMediaSetsToExport, GFSMediaPool. | | [Add-VBRObjectToTapeJob](add-vbrobjecttotapejob.md) | New parameters: GFSScheduleOptions, GFSMediaSetsToExport, GFSMediaPool. | |

Veeam Agent Management

In this version, you can do the following:

* Include to the backup scope data stored in the Music folder on the system volume.
* Enforce Veeam Backup & Replication to trust the provided TLS and root certificates in the certificate chain when you create an object to connect to an Active Directory domain.
* Export installation packages for Microsoft Windows and Linux computers when you generate or download Veeam Installer Service and Veeam Deployer Service certificates and installation packages for Microsoft Windows and Linux computers.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRADDomain](get-vbraddomain.md) | New parameter: Force. | | [Generate-VBRBackupServerDeployerKit](generate-vbrbackupserverdeployerkit.md) | New parameter: AllPlatforms. | | [Get-VBRBackupServerDeployerCertificate](get-vbrbackupserverdeployercertificate.md) | New parameter: AllPlatforms. | | [New-VBRSelectedPersonalFolders](new-vbrselectedpersonalfolders.md) | New parameter: Music. | | [Set-VBRSelectedPersonalFolders](set-vbrselectedpersonalfolders.md) | New parameter: Music. | |

Veeam Plug-Ins for Enterprise Applications

In this version, you can specify storage settings for Veeam Plug-Ins for Enterprise Applications.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRApplicationBackupJob](add-vbrapplicationbackupjob.md) | New parameter: SAPHANAStorageOptions. | | [Set-VBRApplicationBackupJob](set-vbrapplicationbackupjob.md) | New parameter: SAPHANAStorageOptions. | | [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md) | New parameter: OplogProcessingOptions. | | [Set-VBRMongoDBBackupJob](set-vbrmongodbbackupjob.md) | New parameter: OplogProcessingOptions. | | [New-VBRMongoDBDeployment](new-vbrmongodbdeployment.md) | New parameters: ClientCertificatePath, ClientCertificatePassword, CACertificatePath. | | [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) | New parameters: MSSQLEntityType, MSSQL. | | [New-VBROracleRMANStorageOptions](new-vbroraclermanstorageoptions.md) | New parameters: KMSServer, EncryptionKey, EnableEncryption. | | [New-VBRPluginCopyJobStorageOptions](new-vbrplugincopyjobstorageoptions.md) | New parameters: KMSServer, EncryptionKey, EnableEncryption. | | [New-VBRSAPOnOracleStorageOptions](new-vbrsaponoraclestorageoptions.md) | New parameters: KMSServer, EncryptionKey, EnableEncryption. | | [Set-VBRPluginCopyJobStorageOptions](set-vbrplugincopyjobstorageoptions.md) | New parameters: KMSServer, EncryptionKey, EnableEncryption. | |

Page updated 9/8/2025

Page content applies to build 13.0.1.1071
