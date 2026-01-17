---
title: "Performing Restore of VMware Cloud Director VMs"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_vcd_restore.html"
last_updated: "10/29/2024"
product_version: "13.0.1.1071"
---

# Performing Restore of VMware Cloud Director VMs


The VMware Cloud Director VM restore is practically the same as a regular VM restore. You can restore separate VMs to vApps, as well as VM data.

For restore, Veeam Backup & Replication uses VM metadata saved to a backup file and restores specific VM attributes. As a result, you get a fully-functioning VM in VMware Cloud Director, do not need to import the restored VM to VMware Cloud Director and adjust the settings manually.

Backed up objects can be restored to the same VMware Cloud Director hierarchy or to a different Cloud Director environment. For restore or Cloud Director objects from the cloud repository, the following options are supported:

* Full restore for vApps and VMs
* Restore of VM disks
* Restore of VM files
* Guest OS file-level restore for VMs (Microsoft Windows FS only. Multi-OS restore is not supported.)

Related Tasks

* [Performing Entire VM Restore](cloud_connect_vm_restore.md)
* [Restoring VM Files](cloud_connect_vm_files.md)
* [Restoring VM Disks](cloud_connect_disk_restore.md)
* [Restoring VM Guest OS Files](cloud_connect_guest_restore.md)


