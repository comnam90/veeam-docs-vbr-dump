---
title: "How Restore of Regular and Standalone VMs to VMware Cloud Director Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_regular_vm_restore.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# How Restore of Regular and Standalone VMs to VMware Cloud Director Works


Veeam Backup & Replication lets you restore regular VMs that are part of vApps and standalone VMs that were created in the VMware Cloud Director tenant portal.

When you restore regular or standalone VMs back to the VMware Cloud Director hierarchy, the restore process includes the following steps:

1. Veeam Backup & Replication uses the captured vApp metadata to define the vApp settings and VM original location in the VMware Cloud Director hierarchy.
2. Veeam Backup & Replication restores VMs from the backup file to their original location or to a different location. Additionally, Veeam Backup & Replication restores all VM settings.

![How Restore of Regular and Standalone VMs to VMware Cloud Director Works](images/vcd_regular_restore.webp)


