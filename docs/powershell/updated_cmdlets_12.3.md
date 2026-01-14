---
title: "Updated Cmdlets"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/updated_cmdlets_12.3.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Updated Cmdlets

In this article

Managing Security Settings

This section describes changes for Veeam Backup & Replication security settings.

Malware Detection

In this version, you can enable the inline scan for malware detection settings.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Set-VBRMalwareDetectionOptions](set-vbrmalwaredetectionoptions.md) | New parameters added: EnableInlineMalwareScan, DetectionEngine. | |

Backup Infrastructure

This section describes changes for the backup infrastructure settings.

Scale-Out Backup Repositories

In this version, you can enable encryption in the archive tier of the scale-out backup repository.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRScaleOutBackupRepository](add-vbrscaleoutbackuprepository.md) | New parameters added: ArchiveTierEncryptionKey, ArchiveTierKMSServer, EnableArchiveTierEncryption. | | [Set-VBRScaleOutBackupRepositor](set-vbrscaleoutbackuprepository.md) | New parameters added: ArchiveTierEncryptionKey, ArchiveTierKMSServer, EnableArchiveTierEncryption. | |

Object Storage Repositories

In this version, you can deploy multiple buckets in S3 compatible and S3-integrated object storage repositories.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRAmazonS3CompatibleRepository](add-vbramazons3compatiblerepository.md) | New parameters added: EnableBucketAutoProvision, MachinesPerBucketLimit. | | [Set-VBRAmazonS3CompatibleRepository](set-vbramazons3compatiblerepository.md) | New parameters added: EnableBucketAutoProvision, MachinesPerBucketLimit. | |

Replication

This section describes changes for VM replicas.

Failover Plans

In this version, you can specify a timeout in minutes for a CDP replicas failover test.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRFailoverPlan](start-vbrfailoverplan.md) | New parameter added: KeepAliveDuration. | |

Data Recovery

This section describes changes for data recovery operations.

Guest OS File Recovery

In this version, you can specify the temporary Linux helper host when you restore Linux-based or Unix-based guest OS files.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) | New parameter added: HelperHost. | | [Start-VBRCDPLinuxFileRestore](start-vbrcdplinuxfilerestore.md) | New parameter added: HelperHost. | |

Virtual Disks Restore

In this version, the following scenarios are supported:

* You can specify disk mapping settings when perform Hyper-V Instant recovery or restore of Linux-based or Unix-based guest OS files from a CDP replica.
* You can restore VMs as a part of the cluster.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRHvInstantRecovery](start-vbrhvinstantrecovery.md) | New parameter added: DiskMappingRule, RegisterAsClusterResource. | | [Start-VBRHvRestoreVM](start-vbrcdplinuxfilerestore.md) | New parameter added: DiskMappingRule, RegisterAsClusterResource. | |

Unstructured Data Backup

In this version, you can specify backup job mapping settings for file backup jobs and object storage backup job.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRNASBackupJob](add-vbrnasbackupjob.md) | New parameter added: TargetBackup. | | [Set-VBRNASBackupJob](set-vbrnasbackupjob.md) | New parameter added: TargetBackup. | | [Set-VBRObjectStorageBackupJob](set-vbrobjectstoragebackupjob.md) | New parameter added: TargetBackup. | | [Add-VBRObjectStorageBackupJob](add-vbrobjectstoragebackupjob.md) | New parameter added: TargetBackup. | |

VMware Cloud Director

In this version, the Cloud Director providers can use the[Set-VBRvCloudOrganizationJobMapping](set-vbrvcloudorganizationjobmapping.md) cmdlet to make Cloud Director backup jobs, replication jobs and CDP policies visible for their customers in the Veeam Self-Service Backup Portal.

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
