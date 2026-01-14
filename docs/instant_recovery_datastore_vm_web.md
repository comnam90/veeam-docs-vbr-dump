---
title: "Step 6. Select Destination for Virtual Disk Updates"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_datastore_vm_web.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Step 6. Select Destination for Virtual Disk Updates

In this article

The Datastore step of the wizard is available if you have selected Restore to a new location or with different settings at the [Restore Mode](instant_recovery_mode_vm_web.md) step.

At the Datastore step of the wizard, you can select where to store redo logs when a recovered VM is running from a backup. Redo logs are auxiliary files used to keep changes that take place while the recovered VM runs.

By default, redo logs are stored on the [vPower NFS server](vpower_nfs_service.md). You can store redo logs on another datastore in the virtual environment. As soon as a recovery verification job completes, Veeam Backup & Replication deletes redo logs.

To redirect redo logs:

1. Select the Redirect write cache check box.
2. Select a host.
3. Click Datastore and select a datastore from the list.

|  |
| --- |
| Important |
| If the size of recovered VM disks is greater than 2 TB, you must not place redo logs on a VSAN datastore. Otherwise, Veeam Backup & Replication will fail to create a snapshot for the recovered VM. For more information, see [VMware Docs](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/7-0/vsphere-storage-7-0/working-with-datastores-in-vsphere-storage-environment/vsphere-vmfs-datastore-concepts-and-operations/snapshot-formats.html). |

[![Select Datastore - Web UI](images/instant_recovery_datastore_vm_web.webp)](images/instant_recovery_datastore_vm_web.webp "Select Datastore - Web UI")

Page updated 8/29/2025

Page content applies to build 13.0.1.1071
