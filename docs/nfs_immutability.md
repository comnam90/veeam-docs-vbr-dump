---
title: "Immutability for NFS Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/nfs_immutability.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Immutability for NFS Backup Repositories


Veeam Backup & Replication allows you to prohibit deletion of backup files from the NFS shares hosted on WORM-capable storage systems by making that data temporarily immutable. You can enable the immutability feature and specify the immutable period when adding or editing the NFS repository. For more information, see [Configure Backup Repository Settings](nfs_repository_repository.md). Once enabled, immutability prohibits deletion of data from the NFS repository until the immutability expiration date comes. The retention lock is set by committing each backup file to the WORM state using native protocol operations and is enforced by the storage system itself.

Requirements and Limitations for Immutability

Before you enable immutability for a NFS backup repository, check the following requirements and limitations:

* The NFS share must be hosted on the storage system with WORM (Write Once, Read Many) support.

|  |
| --- |
| Important |
| If the storage system does not support WORM, backup files will not be protected from deletion even if the Make recent backups immutable for check box is enabled in the backup repository settings. |

* Do not enable any vendor-configured retention policies on the storage system volume where the NFS share is hosted. Veeam Backup & Replication manages the backup immutability period independently and does not support storage policies. The following types of policies must be disabled on the storage volume:

* Policies that automatically commit files to WORM state
* Minimum retention policies with a non-zero value
* Directory-level retention policies
* Any other policy that automatically sets retention values or controls when files become immutable

* The maximum retention period configured on the storage system must not be lower than the immutability period configured in Veeam Backup & Replication. A higher maximum retention value is recommended.
* Veeam Backup & Replication supports only the file-level retention model (or single file retention). The directory-level retention model is not supported.

How Immutability Works

Immutability for NFS backup repositories is managed by the Veeam Data Mover Service/Veeam Transport Service (veeamtransport). The mechanism works in the following way:

1. For each backup file, Veeam Backup & Replication sets the atime attribute to the configured immutability date using native protocol operations.

The atime attribute contains the last accessed timestamp of the file. On volumes with WORM support, the atime attribute is not updated when files are accessed and is used as the immutability period of the file.

1. Veeam Backup & Replication sets the read-only file attribute to transition the file from writable to immutable state. The timestamp in the atime attribute becomes its immutability period. Once the file is committed to the immutable state, there is only one file attribute that can be modified — the immutability expiration date can be extended. The immutability period cannot be shortened.

For image-level VM and physical machine backups, the immutability period is set according to the following:

* The retention period is counted starting from the moment the last restore point in the active backup chain is created, so that the whole backup chain is marked as immutable for the configured retention period.
* If you increase the immutability period in repository settings, a new value will be applied for the active backup chain and subsequent chains.
* If you decrease the immutability period and a new value for the next restore point is less than the previous one, it will be applied for the next incremental backups in the active chain and for the next chains. For example:

* The immutability period is set for 20 days. The full backup file of the active chain was created on November 1. The first increment was created on November 2. The second increment was created on November 3. Full and incremental backup files will be immutable until November 23: the date of the last restore point creation (November 3) + 20 days.
* If you decrease the immutability period to 7 days on November 4, all previous backup files in the active chain will be immutable until November 23. The next incremental backup in the active chain will be immutable until November 11: the date of the last restore point creation (November 4) + 7 days.

* If you decrease the immutability period and a new value for the next restore point is greater than the previous one, it will be applied for all backup files in the active chain and in the next chains. For example:

* The immutability period is set for 20 days. The full backup file of the active chain was created on November 1. The first increment was created on November 2. The second increment was created on November 3. Full and incremental backup files will be immutable until November 23: the date of the last restore point creation (November 3) + 20 days.
* If you decrease the immutability period to 7 days on November 22, all backup files in the active chain will be immutable until November 29: the date of the last restore point creation (November 22) + 7 days.

* If you use GFS retention policy, see [Retention Scenarios](hardened_repository_immutability.md#retention).

For application-aware processing log backups, the immutability period is set according to the following:

* Newly created log backup files are being updated several times according to the interval settings. Thus, the count of the immutability period starts and the immutability flag is set on the file only when the log backup job finished writing any data to the VLB file.
* The immutability period is not extended for log backup files in the active chain. If there are several chains in the backup, Veeam Backup & Replication also does not extend the immutability for old chains.

|  |
| --- |
| Important |
| If the immutability period is expired for log backup files in the active chain, these files become mutable and may be potentially removed. In this case, the application restore may fail as the log backup chain becomes incomplete. To mitigate risks, make sure that the immutability period covers all backups in the active backup chain. |

* If you increase the immutability period in repository settings, a new value will be applied for all log backup files created after the last successful image-level VM backup or physical machine backup. If you decrease the immutability period, a new value will be applied only for the next log backup files.

* If you use GFS retention policy, see [Retention Scenarios](hardened_repository_immutability.md#retention).

For information on how immutability works for unstructured data backups and enterprise application backups, see the following sections:

* [Unstructured Data Backups in Immutable Repositories](unstructured_data_backup_in_immutable_repo.md)
* [Veeam Plug-In for Oracle RMAN](repos_rman.md#hardened)
* [Veeam Plug-In for SAP HANA](sap_repos.md#hardened)
* [Veeam Plug-In for SAP on Oracle](sap_orcl_repos.md#hardened)
* [Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb_overview_data_backup_repos.md#hardened)
* [Veeam Plug-In for Microsoft SQL Server](repos_mssql.md#hardened)
* [Veeam Plug-In for IBM Db2](db2_backup_repos.md#hardened)

1. When the immutability time period expires, the files can be deleted or modified.

Page updated 2026-08-04

