---
title: "File Backup Integration with Storage Systems"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_snapshot_integration.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# File Backup Integration with Storage Systems


There are two approaches in backing up file shares residing on enterprise NAS storage systems.

Integration with Storage System as NFS or SMB File Share Server

You can add the storage system as a root folder of the server where NFS or SMB file shares reside. The procedure of configuring the file share protection in this case will consist of the following steps:

1. Add the storage system as an NFS file share to the inventory, as described in section [Adding NFS File Share](file_share_backup_add_nfs_file_share.md), or as an SMB fie share, as described in section [Adding SMB File Share](file_share_backup_add_smb_file_share.md). As a file share path, specify the root server folder.

When adding the storage system in this way, you cannot configure what containers, volumes or file shares will be available for further protection. Therefore, to configure them, you must carefully configure inclusion/exclusion settings when creating a file backup job.

Consider that servers accessed by NFS (with file shares and folders within them) and servers accessed by SMB (with file shares and folders within them) are added to the inventory separately. For example, if the storage system IP address is 173.25.136.64, add an NFS share for this server by specifying its root folder as 173.25.136.64:/, and add an SMB share for this server by specifying its root folder as \\173.25.136.64.

|  |
| --- |
| Note |
| If you add a root server folder as a source for protection, hidden and admin file shares are skipped from processing by default. You can enable their processing in the in the configuration file on the Linux-based backup server or with a registry value on the Microsoft Windows-based backup server. For more information, contact [Veeam Customer Support](https://www.veeam.com/support.html). |

1. Create a file backup job, as described in section [Creating File Backup Jobs](file_share_backup_job.md). As a source to protect, you can select the following entities:

* whole server
* file share residing on the server
* separate folders within the share

To protect all file shares residing on one server, you must add to the file backup job both NFS and SMB shares previously added to the inventory.

1. Configure what files and folders must be included in or excluded from processing by the file backup job. For more information on how to include/exclude files and folders from processing, see [Select Files and Folders to Back Up](file_share_backup_job_files_and_folders.md).

Integration with Storage System as NAS Filer

You can add the storage system as a NAS filer. This option is preferable if you want to leverage the backup from storage snapshots technology. For more information, see the [NAS File Share Backup from Storage Snapshots](nas_backup_from_storage_snapshots.md) section.

|  |
| --- |
| Note |
| If you used to protect NFS and SMB file shares residing on the enterprise storage system and added as file shares in inventory, and now you want to protect them using benefits of NAS filer, you can convert backups created for existing SMB or NFS shares into the format of NAS filer shares. For more information, see [Converting Backups from SMB or NFS Shares to NAS Filer Shares](convert_nas_shares_into_san.md). |

The procedure of configuring the file share protection in this case will consist of the following steps:

1. Depending on the type of the NAS system you use, add the storage system to the backup infrastructure, as described in the [Adding NetApp Data ONTAP](netapp_add.md), [Adding Lenovo ThinkSystem DM/DG Series](lenovo_add.md), [Adding Dell PowerScale (formerly Isilon)](dell_powerscale_add.md) or [Adding Nutanix Files Storage](nutanix_add.md) sections.

Depending on storage settings, the IP address for accessing the storage system can differ from one used for accessing it as a server where file shares reside. You can also use the DNS name of the server.

When adding the storage system, make sure that you do not forget to perform the following steps:

1. Enable the NAS filer role for the added storage system.
2. Specify what protocols the storage should use as a NAS filer: NFS or SMB. Only file shares using the selected protocols will be displayed when you add the storage as a NAS filer and thus available for protection.
3. Select storage volumes to analyze for the presence of newly added file shares. You can either configure Veeam Backup & Replication to analyze all storage volumes, or exclude some volumes from processing, or specify only certain volumes that will be processed. Only file shares on the selected storage volumes will be displayed when you add the storage as a NAS filer and thus available for protection.

At this step, you must carefully consider what file shares on what volumes must be protected and through what protocols. Limiting the number of volumes reduces the storage load.

|  |
| --- |
| Note |
| Hidden file shares on storage systems added as NAS filers are processed by default. You can use exclude masks to skip a hidden file share from processing or disable the processing of all hidden file shares in the in the configuration file on the Linux-based backup server or with a registry value on the Microsoft Windows-based backup server. For more information, contact [Veeam Customer Support](https://www.veeam.com/support.html). |

1. Add the configured storage system as a NAS filer to the inventory, as described in section [Adding Enterprise Storage System as NAS Filer](adding_nas_filer.md).
2. Create a file backup job, as described in section [Creating File Backup Jobs](file_share_backup_job.md). As a source to protect, you can select the following entities:

* whole storage
* container (for Dell PowerScale — access zone, for NetApp Data ONTAP — SVM, for Nutanix Files Storage — not applied)
* volume
* file share

You cannot specify separate folders within file shares. Therefore, to configure files and folders to be protected, you must properly configure inclusion/exclusion settings.

1. Configure what files and folders must be included in or excluded from processing by the file backup job. For more information on how to include/exclude files and folders from processing, see [Select Files and Folders to Back Up](file_share_backup_job_files_and_folders.md).


