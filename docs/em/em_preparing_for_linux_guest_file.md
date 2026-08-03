---
title: "Preparing for File Search and Restore (non-Windows machines)"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_preparing_for_linux_guest_file.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Preparing for File Search and Restore (non-Windows machines)


To view, search and restore guest files of non-Windows machines, take the following preparatory steps:

1. To enable guest file indexing, use one of the options of the machine backup job: Index everything, Index everything except, or Index only following folders option. For more information, see the [Guest OS File Indexing](em_indexing_options.md) section of this guide and the [VM Guest OS File Indexing](https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vss_indexing_vm.html?ver=13) section of the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| Guest file indexing is optional. You can browse and restore files from the restore points created without guest indexing. For more information, see [Browsing Machine Backups for Guest OS Files](browsing_vm_backups.md) and [Performing 1-Click File Restore](performing_1-click_file_restore.md).  If you want Veeam Backup Enterprise Manager to display symbolic links to folders when browsing through the machine file system at 1-click file restore, enable indexing in the backup job for that machine. |

1. For proper file system indexing, Veeam Backup & Replication requires several utilities to be installed on the machine: mlocate, gzip, and tar. If these utilities are not found, you are prompted to deploy them to support index creation.
2. By default, guest file restore to the original location is performed using the account specified in the machine backup job. If it does not have sufficient access to target machine, you are prompted to specify another account with sufficient access rights.

For more information, see the [Guest OS Credentials](em_guest_os_credentials.md) section of this guide and the [Specify Guest Processing Settings](https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vss_vm.html?ver=13) section of the Veeam Backup & Replication User Guide.

Preparing Helper Host or Helper Appliance

When restoring guest OS files, Veeam Backup & Replication mounts machine disks from backup or replica to a helper host or appliance. You specify helper host (or appliance) settings on the backup server when you configure guest OS file restore. These settings are saved in the backup server configuration database for the specific user that configured the restore. Before you start file-level restore from Enterprise Manager, ensure the settings are properly configured on the backup server. For more information, see the [Guest OS File Restore](https://helpcenter.veeam.com/docs/vbr/userguide/guest_file_recovery.html?ver=13) section of the Veeam Backup & Replication User Guide.

When you start guest OS file restore from Enterprise Manager, the helper host or appliance is selected according to the following algorithm:

1. Enterprise Manager attempts to obtain the helper host or appliance settings from the configuration database of the backup server.
2. If no helper host or appliance configuration is found for the user account, Veeam Backup & Replication uses the configuration that was last selected at the Helper host step of the Guest File Restore wizard. For details, see the [Specify Helper Host](https://helpcenter.veeam.com/docs/vbr/userguide/multios_restore_host_vm.html?ver=13) section of the Veeam Backup & Replication User Guide.
3. If the Guest File Restore wizard has not been launched, Enterprise Manager checks whether a default Linux mount server is configured on the backup server. If the mount server exists, Enterprise Manager uses it for Linux file restore.
4. If no default Linux mount server is found, Enterprise Manager displays an error.

|  |
| --- |
| Note |
| * Enterprise Manager does not support mounting the restore point to the original host. If the configuration obtained from the backup server is set to original host, Enterprise Manager displays an error. In this case, you must configure a helper host or appliance on the backup server. For details, see the [Specify Helper Host](https://helpcenter.veeam.com/docs/vbr/userguide/multios_restore_host_vm.html?ver=13) section of the Veeam Backup & Replication User Guide. * If you plan to deploy multiple helper appliances to restore machines backed up by different backup servers, their initial configuration must be performed on the backup servers. Centralized configuration from Enterprise Manager is not supported. * If you configure a helper appliance for tenants that will perform self-service restore (from Veeam Self-Service Backup Portal or vSphere Self-Service Backup Portal), be aware that multiple tenants may run the restore procedure at the same time. In this case, if you have configured a static IP address for helper appliances, a tenant will not be able to deploy a helper appliance until the IP address is in use by a helper appliance of another tenant. To let tenants start multiple helper appliances, use a DHCP server in your network and configure the helper appliance to obtain an IP address automatically. |

Page updated 2026-07-21

