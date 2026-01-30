---
title: "Virtual Appliance Mode for VMs on vVol"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/virtual_appliance_mode_vvol.html"
last_updated: "1/23/2025"
product_version: "13.0.1.1071"
---

# Virtual Appliance Mode for VMs on vVol


To transport data of VMs residing on VVol in the Virtual appliance mode, you must assign the VMware backup proxy role to a VM.

The VMware backup proxy VM must meet the following requirement: for VM restore to a VVol in the Virtual appliance mode, the VMware backup proxy VM must be located on the same VVol datastore as the target VM. If this is not possible, the restore proxy must use a different transport mode.

|  |
| --- |
| Note |
| Due to the VMware vSphere mechanisms, data backup and restore for VMs on VVol in the Virtual appliance mode triggers the creation of auxiliary volumes in the storage array:   * A temporary "snapshot" LUN is created when a VMware vSphere snapshot is triggered. The LUN is removed shortly afterward. * An additional "cloned" LUN is created during the data transport. When the VM processing is complete, the LUN is removed.   The maximum amount of volumes depends on the storage array and VMware vSphere limits. For more information, see the documentation of your storage system vendor. |


