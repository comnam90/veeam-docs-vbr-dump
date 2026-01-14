---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/full_restore_before_you_begin.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

Before you restore a VM from a backup, consider the following:

* You can restore a VM from a backup that has at least one successfully created restore point.
* If you back up a VM with vRDM disks, Veeam Backup & Replication converts the disks into VMDK files. Thus, when you restore a VM with a vRDM disk, Veeam Backup & Replication restores this disk as a VMDK file. If you want to preserve the vRDM format for restored disks, use Quick Rollback. For more information, see [Quick Rollback](incremental_restore.md).
* If you want to scan VM data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).
* If you want to run an executable script for a VM, check the [staged restore requirements and limitations](staged_restore_about.md#sr_limitations).
* [For restore to original location] If the original VM has vSphere Fault Tolerance (FT) enabled, you need to reenable FT manually after restore.
* When you restore a VM, consider the Virtual Hardware version compatibility. For more information, see [this VMware KB article](https://kb.vmware.com/s/article/2007240).

Page updated 10/21/2025

Page content applies to build 13.0.1.1071
