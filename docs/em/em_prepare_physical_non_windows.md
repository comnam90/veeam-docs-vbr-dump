---
title: "Non-Windows Server"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_prepare_physical_non_windows.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---

# Non-Windows Server


Preparing Backup

You can restore files from a backup of a physical server created with or without indexing.

|  |
| --- |
| Note |
| Veeam Agent for Mac and Veeam Agent for Linux on Power do not support file system indexing. |

To prepare a backup with guest file indexing:

1. Check for the following utilities to be installed on the server: mlocate, gzip, and tar. These utilities are required for file indexing. When you enable file indexing, Veeam Agent will prompt you to deploy them in case they are not found.
2. Enable guest file system indexing in the backup job settings.

For more information, see the File System Indexing section of the following guides:

* [Veeam Agent for Linux User Guide](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_index.html?ver=13)
* [Veeam Agent for Oracle Solaris User Guide](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/backup_job_index.html?ver=13)
* [Veeam Agent for IBM AIX User Guide](https://helpcenter.veeam.com/docs/agentforaix/userguide/backup_job_index.html?ver=13)

1. Run the backup job with guest file system indexing enabled.
2. Make sure the indexing data is imported to Veeam backup database, and catalog data replication is completed successfully. For more information, see [Performing Catalog Replication and Indexing](performing_catalog_replication.md).

Whether you restore from a backup with or without guest file indexing, prepare a machine to operate as a helper host or helper appliance.

Preparing Helper Host or Helper Appliance

When restoring guest OS files, Veeam Backup & Replication mounts machine disks from the backup or replica to a mount server (helper host or helper appliance). For the mount server, you can use a machine running on VMware or Microsoft Hyper-V. You specify mount server settings on the backup server when you configure a backup job for the machine. These settings are saved in the Veeam Backup & Replication database on per-user basis. The settings are applied each time the user starts file-level restore. For more information on the helper host and helper appliance, see the [Guest OS File Restore](https://helpcenter.veeam.com/docs/vbr/userguide/guest_file_recovery.html?ver=13) section of the Veeam Backup & Replication User Guide.

When you start guest OS file restore from Veeam Backup Enterprise Manager, the mount server settings are obtained from the configuration database of the backup server. If no helper host or helper appliance configuration is found for the user account, Veeam Backup & Replication uses the configuration set during the latest file-level restore performed on the backup server. Thus, before you start file-level restore from Enterprise Manager, make sure the mount server settings are configured on the backup server with which Veeam Agent is integrated.

|  |
| --- |
| Note |
| If you plan to deploy multiple helper appliances to restore machines backed up by Veeam Agents integrated with different backup servers, their initial configuration must be performed on the backup servers. Centralized configuration from Veeam Backup Enterprise Manager is not supported. |

Other Prerequisites

1. Make sure that the DNS name of the target (original) server where you plan to restore the files is resolved properly.
2. During guest file restore to the original location, you are prompted for the credentials to access the target server. Specify a user name and password or private key for the account with sufficient access rights.


