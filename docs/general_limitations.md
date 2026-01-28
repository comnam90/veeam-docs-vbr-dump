---
title: "General Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/general_limitations.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# General Considerations and Limitations


This section contains general limitations for object storage repositories:

* You can add an object storage repository to a second backup server using credentials with the read-only access permissions that allows you to perform data recovery options. If you use credentials with full-access permissions, it will lead to unpredictable behavior and data loss. For more information on permissions, see [Permissions](required_permissions.md#s3readonly).

|  |
| --- |
| Important |
| Consider the following:   * This option is not supported for Microsoft Azure Storage and Veeam Data Cloud Vault. * This option works for object storage repositories only if they meet the following requirements:  * You plan to add these object storage repositories as a performance or capacity extent of a scale-out backup repository.  * The object storage repositories do not have data encryption enabled. If encryption is enabled on these repositories, you will not be able to add object storage repositories using credentials with read-only permissions.  * You can use this option for direct backup object storage repositories added either as a standalone repository or a performance extent of a scale-out backup repository. |

* Data in an object storage bucket or container must be managed solely by Veeam Backup & Replication, including retention and data management. If you enable Object Lock and Versioning features on an S3 bucket or version-level WORM on an Azure container, make sure that you do NOT enable the default retention option. Enabling lifecycle rules is not supported, and may result in backup and restore failures.

* You cannot simultaneously store [capacity tier](capacity_tier.md) and [unstructured data](unstructured_data_backup.md) backups in the same object storage repository. You must either add this object storage repository as the capacity extent or use it as the backup repository for the unstructured backup job.

|  |
| --- |
| Important |
| One object storage repository must not be used across multiple Veeam Backup & Replication servers since it leads to unpredictable system behavior and data loss. For example, you must not use one object storage to store backups of file shares on two different backup servers. |

* The backup proxy that processes backup data must meet the following requirements:

* It must be an on-premises server as close as possible to a backup server.
* It must have access to the cloud storage that you use as an object storage repository.

* You cannot switch an object storage repository to [Sealed Mode](sobr_seal.md) and to [Maintenance Mode](sobr_maintenance.md) unless it is an extent of a scale-out backup repository.

* Scale-out backup repositories and Veeam Cloud Connect repositories are not supported as a backup destination for cloud machines.

Ports and Network

Consider the following network limitations:

* Ensure that you open the required ports to communicate with object storage repositories in advance. Consider that non-internet-facing infrastructure components (for example, a gateway server or a backup proxy) must have internet access to verify that the certificates installed on object storage repositories are valid. For more information, see [Ports](used_ports.md#osrc). If these components do not have access to the Internet to perform certificate revocation checks, disable them by modifying the registry (for Windows-based servers) or the etc/VeeamAgentConfig file (for Linux-based servers). For more information, see [this Veeam KB article](https://www.veeam.com/kb4373), step 6.

* If you use default network security configuration for helper appliances, make sure that they are compliant with your internal security policies.

* Object storage gateway appliances that are used to store backup data in filer (SMB (CIFS)/NFS) or block device mode (iSCSI/FC/SAS) are not supported if the backup data is offloaded to object storage and is no longer stored directly on the appliance.

Such gateway appliances are only supported in the following cases:

* All of the backup data is stored on the appliance altogether (that is, all of the backup chains are stored on the appliance as a whole and not scattered across multiple devices) and only additional copies of the backup data is transported to object storage.
* These appliances emulate a tape system (VTL) as an access protocol for Veeam Backup & Replication.

Security Limitations

Multi-factor authentication (MFA) is not supported for object storage repositories.

Limitations for Backup Processing

Consider the following limitations for backup processing:

* If a backup chain contains backup files that are marked as corrupted by [Health Check](backup_health_check.md), then such corrupted files, as well as all subsequent files that go after the corrupted one are never [offloaded](capacity_tier_data_transfer.md). In such a scenario, offload is only possible starting from the full backup file that succeeds the backup chain with corrupted backups.
* For optimal processing, we recommend to set the default block size to 1MB in the storage settings of a backup job. Larger block size can lead to multiple times larger incremental backups, while smaller block sizes will create extra IO pressure on the object storage. For more information, see [Storage Optimization](compression_deduplication.md#optimization).

* The [periodic compact of full backup file](backup_compact_file.md) option is not available.
* By default, Veeam Backup & Replication uses the [forever forward incremental method](incremental_forever_backup.md) to back up directly to object storage repositories. If you want to create a new full backup, enable the [long-term retention policy (GFS)](gfs_retention_policy.md). In this case, Veeam Backup & Replication will create [synthetic full backups](synthetic_full_backup.md) and, therefore, will produce a [forward incremental backup chain](forward_incremental_backup.md).

|  |
| --- |
| Note |
| To produce an independent full backup, you can also run the active full backup manually or specify a periodic schedule for it. Note that this method will significantly increase object storage space consumption. |

Deployment Considerations and Limitations

Consider the following deployment imitations:

* Make sure that a proxy server that you plan to use, meets the System Requirements for a [VMware vSphere proxy server](system_requirements.md#proxy) or a [Hyper-V off-host proxy server](system_requirements.md#offhost_proxy) depending on the protected platform.
* You must locate your proxy server as close as possible to the backup source host.
* Veeam Agent transfers data to the object storage repositories without a proxy server. Make sure that you grant Veeam Backup & Replication and Veeam Agent necessary permissions. For more information on how to configure permissions within Veeam Backup & Replication, see [Access Permissions](access_permissions.md#s3permissions). For more information on how to configure permissions for Veeam Agent, see the [Permissions](agents_permissions.md#s3) section in Veeam Agent Backup. For more information on how Veeam Agent works in direct connection with object storage repositories, see the [Access Permissions](agents_object_storage_direct_access.md#S3) section in Veeam Agent Backup.
* [For backup copy jobs and file backup copy jobs] Veeam Backup & Replication uses the source backup repository as the gateway server. For more information, see the [Automatic Gateway Selection](gateway_server.md#auto) section.

* Veeam Data Cloud Vault does not support immutability for Veeam Agents that use direct connection to transfer data to object storage repositories.

* If you use default network security configuration for helper appliances, make sure that they are compliant with your internal security policies.

* Within a scale-out backup repository, the mount server of a performance extent will act as a gateway server of the capacity extent if all of the following is true:

1. You use SMB share/NFS share/deduplicating storage appliances as performance extents of your scale-out backup repository.
2. You have chosen Automatic selection for the gateway server at the [Specify Shared Folder Settings](repository_server.md) step of the New backup repository wizard.
3. For the object storage that you use as the capacity extent, you have not selected to connect to object storage using a gateway server at the Account step of the New Object Repository wizard.

Limitations for Veeam Solutions

For more information on limitations for Veeam solutions that utilizes object storage repositories functionality, see the following sections of the necessary guide:

* [Veeam Agent Backup](agents_object_storage.md#limits) — to check limitations for Veeam Agent management solution.
* [Veeam Agent for Microsoft Windows](https://helpcenter.veeam.com/docs/agentforwindows/userguide/backup_to_object_storage.html?ver=13#considerations-and-limitations) — to check limitations for data protection and disaster recovery solution for physical and virtual machines running Windows-based operating systems.
* [Veeam Agent for Linux](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_external_cloud.html?ver=13#considerations-and-limitations) — to check limitations for data protection and disaster recovery solution for physical endpoints and virtual machines running Linux-based operating systems.
* [Veeam Agent for Mac](https://helpcenter.veeam.com/docs/agentformac/userguide/backup_object_ovw.html?ver=13#considerations-and-limitations) — to check limitations for data protection and disaster recovery solution for physical endpoints and virtual machines running macOS.
* [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/vbr/cloud/cc_object_storage.html?ver=13#considerations-and-limitations) — to check limitations for data protection and disaster recovery solution for cloud service providers.


