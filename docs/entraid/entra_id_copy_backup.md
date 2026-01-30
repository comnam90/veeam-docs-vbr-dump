---
title: "Copying Log Backups"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_copy_backup.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Copying Log Backups


This section applies to log backups only.

Copying backups can be helpful if you want to copy audit and sign-in log backups to a repository, or local or shared folder. Veeam Backup & Replication copies the whole backup chain.

When Veeam Backup & Replication performs the copy operation, it disables the job, copies files to the target location and then enables the job. After the copy operation finishes, the copied backups are shown in a node with the (Exported) postfix in the inventory pane.

|  |
| --- |
| Note |
| This section is about one-time copy operation. If you want to copy backups on a schedule, configure the [secondary destination](entra_id_log_job_secondary.md) on the job settings. |

Copying Backups

To copy log backups, do the following:

1. Open the Home view.
2. In the inventory pane, select the Backups node.
3. In the working area, select the necessary job.
4. Right-click the job and select Copy backup. Alternatively, click Copy Backup on the ribbon.
5. In the Copy Backup to Another Location window, choose a repository to which you want to copy backups.
6. Click OK.

After the copy process finishes, the copied backups are shown in the Disk (Exported) node in the inventory pane.

|  |
| --- |
| Note |
| Consider the following:   * If you copy backups from a scale-out backup repository and some backups are stored on extents in the Maintenance mode, such backups are not copied.  * Veeam Backup & Replication copies backups only from the performance tier of the scale-out backup repository. If you want to copy data from the capacity tier, you first need to download it to the performance tier. For more information, see the [Downloading Data from Capacity Tier](https://helpcenter.veeam.com/docs/vbr/userguide/downloading_from_capacity_tier.html?ver=13) section in the Veeam Backup & Replication User Guide. |

![Copying Log Backups](images/entra_id_copy_backup.webp)


