---
title: "Step 5. Select Storage Container"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_to_ahv_container.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Select Storage Container


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Storage Container step of the wizard, choose the storage container where virtual disks of the recovered VM will be stored.

For a container to be displayed in the list of the available containers, it must be configured in the Nutanix AHV cluster as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism:wc-storage-management-wc-c.html).

|  |
| --- |
| Note |
| You cannot choose a storage container when restoring the VM from a snapshot. |

![Step 5. Select Storage Container](images/ahv_restore_vm_container.webp)

Page updated 2026-04-22

