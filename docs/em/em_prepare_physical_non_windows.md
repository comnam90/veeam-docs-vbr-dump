---
title: "Non-Windows Server"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_prepare_physical_non_windows.html"
last_updated: "2026"
product_version: "13.1.0.411"
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

When restoring guest OS files, Veeam Backup & Replication mounts machine disks from the backup or replica to a mount server (helper host or helper appliance). For the mount server, you can use a machine running on VMware vSphere or Microsoft Hyper-V. You specify helper host (or appliance) settings on the backup server when you configure guest OS file restore. These settings are saved in the backup server configuration database for the specific user that configured the restore. Before you start file-level restore from Enterprise Manager, ensure the settings are properly configured on the backup server. For more information, see the [Guest OS File Restore](https://helpcenter.veeam.com/docs/vbr/userguide/guest_file_recovery.html?ver=13) section of the Veeam Backup & Replication User Guide.

When you start guest OS file restore from Veeam Backup Enterprise Manager, the mount server settings are obtained from the configuration database of the backup server. If no helper host or helper appliance configuration is found for the user account, Veeam Backup & Replication uses the configuration set during the latest file-level restore performed on the backup server. Thus, before you start file-level restore from Enterprise Manager, make sure the mount server settings are configured on the backup server with which Veeam Agent is integrated.

When you start guest OS file restore from Enterprise Manager, the helper host or appliance is selected according to the following algorithm:

1. Enterprise Manager attempts to obtain the helper host or appliance settings from the configuration database of the backup server.
2. If no helper host or appliance configuration is found for the user account, Veeam Backup & Replication uses the configuration that was last selected at the Helper host step of the Guest File Restore wizard. For details, see the [Specify Helper Host](https://helpcenter.veeam.com/docs/vbr/userguide/multios_restore_host_vm.html?ver=13) section of the Veeam Backup & Replication User Guide.
3. If the Guest File Restore wizard has not been launched, Enterprise Manager checks whether a default Linux mount server is configured on the backup server. If the mount server exists, Enterprise Manager uses it for Linux file restore.
4. If no default Linux mount server is found, Enterprise Manager displays an error.

|  |
| --- |
| Note |
| If you plan to deploy multiple helper appliances to restore machines backed up by Veeam Agents integrated with different backup servers, their initial configuration must be performed on the backup servers. Centralized configuration from Veeam Backup Enterprise Manager is not supported. |

Other Prerequisites

1. Make sure that the DNS name of the target (original) server where you plan to restore the files is resolved properly.
2. During guest file restore to the original location, you are prompted for the credentials to access the target server. Specify a user name and password or private key for the account with sufficient access rights.

Page updated 2026-07-22

