---
title: "Data Recovery for VMware Cloud Director"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_vm_restore.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Data Recovery for VMware Cloud Director

In this article

Veeam Backup & Replication enables full-fledged restore of VMs to VMware Cloud Director. You can restore separate VMs to vApps, as well as VM data.

For restore, Veeam Backup & Replication uses VM metadata saved to a backup file and restores specific VM attributes. As a result, you get a fully-functioning VM in VMware Cloud Director, do not need to import the restored VM to VMware Cloud Director and adjust the settings manually.

Backed-up objects can be restored to the same VMware Cloud Director hierarchy or to a different VMware Cloud Director environment. Restore options include:

* Instant Recovery
* Full restore for vApps and VMs
* Restore of VM disks
* Restore of VM files
* Guest OS file restore for VMs

In This Section

* [VM Recovery](vcd_vm_restore.md)
* [vApp Recovery](vcd_vapp_recovery.md)
* [Item Recovery](vcd_item_recovery.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
