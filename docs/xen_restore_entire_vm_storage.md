---
title: "Step 5. Select Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_restore_entire_vm_storage.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Select Storage


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Storage step of the wizard, choose a datastore where virtual disks of the recovered VM will be stored. For a datastore to be displayed in the list of available storage, it must be configured in the virtual environment.

If you restore the VM to the original pool, Veeam Backup & Replication will automatically select the same datastore where the original VM disks were stored at the moment of backup. If you restore the VM to a new pool, you will have to select a datastore manually.

![Step 5. Select Storage](images/xen_restore_entire_vm_storage.webp)

Page updated 2026-07-10

