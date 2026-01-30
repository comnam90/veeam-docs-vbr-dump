---
title: "Maintenance Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_advanced_main_linux.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Maintenance Settings


You can specify maintenance settings for a backup chain created with the Veeam Agent backup job managed by the backup server. Maintenance operations help make sure that the backup chain remains valid and consistent.

To specify maintenance settings for the backup job:

1. In the Advanced Settings window, select the Maintenance tab.
2. To periodically perform a health check for the latest restore point in the backup chain, in the Storage-level corruption guard section select the Perform backup files health check check box and click Configure to specify the time schedule for the health check.

An automatic health check can help you avoid a situation where a restore point gets corrupted, making all dependent restore points corrupted, too. If during the health check Veeam Backup & Replication detects corrupted data blocks in the latest restore point in the backup chain (or the restore point before the latest one if the latest restore point is incomplete), it will start the health check retry and transport valid data blocks from the protected computer to the Veeam backup repository. The transported data blocks are stored to a new backup file or the latest backup file in the backup chain, depending on the data corruption scenario. For more information, see [Health Check for Backup Files](backup_health_check.md).

|  |
| --- |
| NOTE |
| The Defragment and compact full backup file option is not available for backup jobs targeted at object storage. For object storage, Veeam Agent offers a special health check mechanism as default. To run the health check for object storage, enable the Perform backup files health check option in the Storage-level corruption guard section and specify the health check schedule.  You can also switch from the health check for object storage to the standard health check. To do so, select the Verify content of each object in backup check box in the backup job settings. Keep in mind that enabling this setting may result in additional charges from your object storage provider.  For more information, see the [Health Check for Object Storage](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_health_check.html?ver=13) section in the Veeam Agent for Linux User Guide. |

1. Select the Remove deleted items data after check box and specify the number of days for which you want to keep the backup created with the backup job in the target location.

For Veeam Agent backup jobs managed by the backup server, deleted items retention policy is similar to retention policy for deleted VMs. After you remove a protection group or individual computer from a Veeam Agent backup job, Veeam Backup & Replication will keep its data on the backup repository for the period that you have specified. When this period is over, backup data of this computer will be removed from the backup repository. For more information, see [Retention Policy for Deleted Items](retention_deleted_vms.md).

By default, the deleted items data retention period is 30 days. Do not set the deleted items retention period to 1 day or a similar short interval. In the opposite case, the backup job may work not as expected and remove data that you still require.

1. To periodically compact a full backup, select the Defragment and compact full backup file check box and click Configure to specify the schedule for the compact operation.

|  |
| --- |
| NOTE |
| The Defragment and compact full backup file option is not available for backup jobs targeted at object storage. |

During the compact operation, Veeam Backup & Replication creates a new empty file and copies to it data blocks from the full backup file. As a result, the full backup file gets defragmented and the speed of reading and writing from/to the backup file increases.

If the full backup file contains data blocks for deleted items (protection groups or individual computers), Veeam Backup & Replication removes these data blocks. For more information, see [Compact of Full Backup File](backup_compact_file.md).

|  |
| --- |
| ![Maintenance Settings](images/icon_note.webp)NOTE |
| Consider the following:   * If you want to periodically compact a full backup, you must make sure that you have enough free space in the target location. For the compact operation, the amount of free space must be equal to or more that the size of the full backup file. * In contrast to the compact operation for a VM backup, during compact of a full Veeam Agent backup file, Veeam Backup & Replication does not perform the data take out operation. If the full backup file contains data for a machine that has only one restore point and this restore point is older than 7 days, Veeam Backup & Replication will not extract data for this machine to a separate full backup file. |

![Maintenance Settings](images/agent_job_settings_maintain_linux.webp)


