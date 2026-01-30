---
title: "Data Exclusion"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_exclusion.html"
last_updated: "3/4/2025"
product_version: "13.0.1.1071"
---

# Data Exclusion


When you configure a backup or replication job, you can define what data you want to back up and replicate and exclude data you do not need. Data exclusion helps reduce the size of the VM backup or replica and decrease the load on the network.

You can exclude data at the VM level and at the VM guest OS level.

At the VM level:

* [VMs added as part of the container](exclude_vms.md#container)
* [VM disks](exclude_vms.md#disks)
* [VM templates](exclude_vms.md#template) (only for backup)

At the VM guest OS level:

* [Swap files on the VM guest OS](swap_files.md)
* [Deleted file blocks on the VM guest OS (BitLooker)](dirty_blocks.md)
* [Files and folders on the VM guest OS](guest_file_exclusion.md)

|  |
| --- |
| Note |
| To reduce the size of the backup file, Veeam Backup & Replication automatically excludes VM log files from processing. |


