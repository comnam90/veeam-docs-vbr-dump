---
title: "Data Exclusion"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_exclusion_hv.html"
last_updated: "3/3/2025"
product_version: "13.0.1.1071"
---

# Data Exclusion

In this article

When you configure a backup or replication job, you can define what data you want to back up and replicate and exclude data you do not need. Data exclusion helps reduce the size of the VM backup or replica and decrease the load on the network.

You can exclude data at the VM level and at the VM guest OS level.

At the VM level:

* [VMs added as part of the container](exclude_vms_hv.md)
* [VM disks](exclude_vms_hv.md)

At the VM guest OS level:

* [Swap files on the VM guest OS](swap_files_hv.md)
* [Deleted file blocks on the VM guest OS (BitLooker)](dirty_blocks_hv.md)
* [Files and folders on the VM guest OS](guest_file_exclusion_hv.md)

Page updated 3/3/2025

Page content applies to build 13.0.1.1071
