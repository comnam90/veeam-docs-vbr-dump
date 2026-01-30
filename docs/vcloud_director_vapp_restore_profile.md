---
title: "Step 8. Select Storage Policy and Datastores"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_vapp_restore_profile.html"
last_updated: "5/26/2023"
product_version: "13.0.1.1071"
---

# Step 8. Select Storage Policy and Datastores


The Datastores step of the wizard is available if you have chosen to change settings of the restored vApp, for example, its name or location.

To select a storage policy for the vApp:

1. Select the vApp in the list and click Policy.
2. In the displayed window, select the necessary policy for the vApp.

If you have selected to disable fast provisioning at the previous step of the wizard, you must select a datastore on which the disks of restored VMs will be placed. To do this:

1. Select VM or vApp in the list and click Datastore.
2. In the displayed window, select the datastore on which the disks of the VM must be placed.

![Step 8. Select Storage Policy and Datastores](images/vcloud_restore_datastores.webp)


