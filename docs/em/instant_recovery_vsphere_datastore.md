---
title: "Step 5. Specify Datastore"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/instant_recovery_vsphere_datastore.html"
last_updated: "9/4/2025"
product_version: "13.0.1.1071"
---

# Step 5. Specify Datastore


The Datastore step of the wizard is available if you recover a VM to a new location or with different settings.

At this step of the wizard, you can select where to store redo logs when a VM is running from the backup. Redo logs are auxiliary files used to keep changes that take place while the recovered VM runs.

By default, redo logs are stored in vPower NFS datastore. You can store redo logs in any datastore in the virtual environment if necessary. Redirecting redo logs improves recovery performance but makes Storage vMotion not possible for ESXi 5.5. As soon as a recovery verification job completes, Veeam Backup & Replication deletes redo logs. For more information on vPower NFS datastore, see the [vPower NFS Service](https://helpcenter.veeam.com/docs/vbr/userguide/vpower_nfs_service.html?ver=13) section of the Veeam Backup & Replication User Guide.

To redirect redo logs, do the following:

1. Select the Redirect write cache check box.
2. Click Choose and select a datastore.

![Step 5. Specify Datastore](images/instant_recovery_vmware_datastore.webp "Specifying Datastore")


