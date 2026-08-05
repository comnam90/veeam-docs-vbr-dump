---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_to_ahv_byb_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you perform Nutanix AHV VM restore, consider the following limitations:

* When restoring the VM from a backup, Veeam Plug-in for Nutanix AHV stores all virtual disks of the recovered VM in one storage container.

* When restoring a VM from a [snapshot, backup snapshot or PD snapshot](ahv_nutanix_snapshots.md), Veeam Plug-in for Nutanix AHV stores virtual disks of the recovered VM in the original storage container.
* When restoring a VM from a [snapshot or PD snapshot](ahv_nutanix_snapshots.md), Veeam Plug-in for Nutanix AHV retains the original VM network settings. After the VM is restored, you can change these settings using the Nutanix Prism console as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v6_5:ahv-vm-nw-mgmt-c.html).

* When restoring a VM to a new location, Veeam Plug-in for Nutanix AHV does not restore the VM affinity policy configuration. Therefore, you must manually configure the affinity policy as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v6_5:ahv-affinity-policies-c.html).

Page updated 2026-04-10

