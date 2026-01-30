---
title: "Step 6. Select Target Datastore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/failback_datastore_vm.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Step 6. Select Target Datastore


The Datastore step is available if you have selected the Failback to the specified location option at the [Destination](failback_destination_vm.md) step.

At the Datastore step of the wizard, specify datastores where you want to store configuration files and disk files of VMs that will be recovered. Also, you can change disk types.

1. To change a datastore where VM files will be stored, select the necessary VMs and click Datastore. From the list of available datastores, select the necessary datastore.

If configuration and disk files of VMs must be placed to different datastores, select files of the necessary type, click Datastore and select the necessary datastore.

1. To change disk type settings, select the necessary disk files and click Disk Type. In the Disk Type Settings window, select the necessary disk type. For more information about disk types, see [VMware docs](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-4C0F4D73-82F2-4B81-8AA7-1DD752A8A5AC.html).

By default, Veeam Backup & Replication preserves disk types of the source VMs.

|  |
| --- |
| Note |
| You can change disk types only for VMs with Virtual Hardware version 7 or later. |

![Step 6. Select Target Datastore](images/failback_6.webp)


