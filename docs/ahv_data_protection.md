---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_data_protection.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup


With Veeam Backup & Replication, you can protect data with image-level backups. An image-level backup captures the whole image of the processed VM (including VM configuration, OS data, application data and so on) at a specific point in time.

To create backups, Veeam Plug-in for Nutanix AHV uses [workers](ahv_workers.md) that retrieve VM data from the cluster and forward it to a backup repository in the [native Veeam format](ahv_backup.md). You can use the backup to restore the VM to the original Nutanix AHV environment or any other supported virtual environment, for example, VMware or Hyper-V. To create a VM backup, [configure a backup job](ahv_backup_job_create.md) or [perform a VeeamZIP operation](ahv_veeamzip_backup_create.md).

|  |
| --- |
| Note |
| To back up data that resides on Nutanix Files, use the Veeam Backup & Replication file share backup functionality described in section [Unstructured Data](unstructured_data_backup.md). |

Page updated 2026-06-11

