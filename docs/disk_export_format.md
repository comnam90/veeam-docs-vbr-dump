---
title: "Step 5. Select Destination and Disk Format"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/disk_export_format.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# Step 5. Select Destination and Disk Format


At the Target step of the wizard, select the destination for disk export and format in which you want to save the resulting virtual disks:

1. From the Server list, select a server on which the resulting virtual disks must be saved. If you plan to save the disks to a datastore, select a host to which this datastore is connected.

|  |
| --- |
| Note |
| Consider the following:   * You cannot select the backup server as the target for recovery due to security reasons. * If you select to export the resulting virtual disk to an ESXi datastore, you can save the virtual disk in the VMDK format only. Other options are disabled. * If you export disks as VMDK to a vSAN datastore, disk are exported according to the storage policy set on the datastore. * If you export disks as VMDK to a place other than an ESXi datastore, disks are exported as thick provision lazy zeroed. |

1. In the Path to folder field, specify a datastore or folder on the server where the virtual disks must be placed.
2. Select the export format for the disks:

* VMDK — select this option if you want to save the resulting virtual disk in the VMware VMDK format. This is the only available option if you export disks to an ESXi datastore.
* VHD — select this option if you want to save the resulting virtual disk in the Microsoft Hyper-V VHD format.
* VHDX — select this option if you want to save the resulting virtual disk in the Microsoft Hyper-V VHDX format (supported by Microsoft Windows Server 2012 or later).

1. [For disks exported as VMDK to an ESXi datastore] Click the Pick proxy to use link to select backup proxies over which disk data must be transported to the target datastore. You can assign backup proxies explicitly or instruct Veeam Backup & Replication to automatically select backup proxies.
2. From the Disk Type drop-down list, select a disk type for the exported disks.

![Step 5. Select Destination and Disk Format](images/disk_export_disks_type.webp)


