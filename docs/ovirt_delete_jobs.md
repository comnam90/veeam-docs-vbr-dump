---
title: "Deleting Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_delete_jobs.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Deleting Backup Jobs


You can permanently delete a backup job from the Veeam Backup & Replication configuration database if you no longer need it. When you delete a job, backups created by this job are displayed under the Backups > Disk (Orphaned) node in the Home view of the Veeam Backup & Replication console.

To delete a backup job, do the following:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, right-click the necessary job and select Delete.

Alternatively, select the job and click Delete on the ribbon.

|  |
| --- |
| Tip |
| If you want to delete backup files as well, follow the instructions provided in section [Deleting Backups](ovirt_retention.md). |

[![Deleting Backup Jobs](images/ovirt_vbr_delete_job.webp)](images/ovirt_vbr_delete_job.webp "Deleting Backup Jobs")


