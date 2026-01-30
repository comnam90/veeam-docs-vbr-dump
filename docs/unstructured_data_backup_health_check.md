---
title: "Performing Health Check and Repair for Unstructured Data Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/unstructured_data_backup_health_check.html"
last_updated: "10/3/2025"
product_version: "13.0.1.1071"
---

# Performing Health Check and Repair for Unstructured Data Backups


In this section you will learn how to perform:

* [Health check for file share backup files](#nas_health_check)
* [Repair of file share backup files](#nas_repair)

Health Check for File Share Backup Files

You can manually perform a health check for the backup chain. During the health check, Veeam Backup & Replication performs a CRC check for metadata and a hash check for data blocks in backup files to verify their integrity. The health check helps make sure that the restore point is consistent, and you will be able to restore data from this restore point.

To run the health check:

1. Open the Home view.
2. In the inventory pane, select Jobs > Backup. Alternatively, select Backups.
3. In the working area, select a job of the File Backup or Object Storage Backup type and click Run Health Check on the ribbon or right-click the job and select Run health check.

To run the health check periodically, you must enable the Perform backup files health check option in the backup job settings and define the health check schedule. By default, the health check is performed on the last Friday of every month. You can change the schedule and run the health check weekly or monthly on specific days. To learn how to configure periodic health check, see [Maintenance Settings](file_share_backup_job_advanced_maintenance.md).

|  |
| --- |
| Important |
| If you store your file backups on public cloud object storage repositories, running the health check operations may result in constantly downloading and uploading data to and from the storage, which may lead to higher costs. To avoid this, use helper appliances, configured for the repositories within the public clouds. For more information, see the [Unstructured Data Backups in Object Storage Repositories](unstructured_data_backup_in_object_storage.md) section. |

[![Run Health Check](images/nas_health_check.webp)](images/nas_health_check.webp "Run Health Check")

Repair of File Share Backup Files

If during the health check Veeam Backup & Replication detects some inconsistency in the file share backup files, you can run the backup repair procedure to fix the issues.

To run the backup repair:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select a job of the File Backup type, right-click the job and select Repair backup.

[![Run Repair](images/nas_repair_backup.webp)](images/nas_repair_backup.webp "Run Repair")


