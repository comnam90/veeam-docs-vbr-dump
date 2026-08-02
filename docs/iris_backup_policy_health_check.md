---
title: "Running Backup Policy Health Check"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_backup_policy_health_check.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Running Backup Policy Health Check


You can run a health check for an existing InterSystems IRIS application backup policy. During the health check, Veeam Backup & Replication performs a CRC check for metadata and a hash check for data blocks in backup files to verify their integrity. The health check confirms that the restore point is consistent and that data can be restored from it. For details about how the health check works, see [How Health Check Works](pve_how_health_check_works.md).

|  |
| --- |
| NOTE |
| The health check applies only to application backup policies that run in backup mode. In snapshot-only mode, no backup files are created and the health check is not available. |

To run the health check manually:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the InterSystems IRIS application backup policy and click Run Health Check on the ribbon, or right-click the policy and select Run health check.

To run the health check periodically, enable the Perform backup files health check option in the policy advanced settings and define a schedule. By default, the health check runs on the last Friday of every month. You can change the schedule to run weekly or monthly on specific days. For details, see [Maintenance Settings](iris_policy_advanced_maintenance.md).

|  |
| --- |
| Important |
| If you store InterSystems IRIS backups in a public cloud object storage repository, running the health check may result in downloading and uploading data to and from the storage, which may increase costs. To reduce costs, configure a helper appliance for the object storage repository. For more information, see [Backup to Object Storage](iris_object_storage.md). |

Page updated 2026-06-24

