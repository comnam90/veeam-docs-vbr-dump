---
title: "Step 6. Select Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_restore_entire_vm_storage.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Select Storage


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Storage step of the wizard, choose storage where virtual disks of the recovered VM will be stored. For storage to be displayed in the list of available storage, it must be configured in the virtual environment.

If you restore the VM to the original cluster, Veeam Backup & Replication will automatically select the same storage where the original VM disks were stored at the moment of backup. If you restore the VM to a new cluster, you will have to select storage manually. In both cases, the restored disks will by default have the same type as the original VM disks; however, you can specify another type manually.

|  |
| --- |
| Note |
| You will not be able to select storage and disk type for each VM disk separately. |

![Step 6. Select Storage](images/sangfor_restore_entire_vm_storage.webp)

Page updated 2026-07-16

