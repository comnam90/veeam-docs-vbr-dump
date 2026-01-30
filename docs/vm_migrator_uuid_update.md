---
title: "Step 2. Update Existing VMs BIOS UUIDs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_migrator_uuid_update.html"
last_updated: "2/28/2025"
product_version: "13.0.1.1071"
---

# Step 2. Update Existing VMs BIOS UUIDs


This is an optional step that can be performed to update the BIOS UUIDs of existing VM entries within the Veeam Backup & Replication configuration database based on information from the old vCenter, ensuring future matching accuracy. Skip this step if the old vCenter is no longer operational or if you have already migrated VMs to the new vCenter.

To update BIOS UUIDs of VMs, run the Set-VBRVmBiosUuid cmdlet and specify the VCenterName parameter value.

This example shows how to update BIOS UUIDs of VMs located on the old vCenter named vcenter70.

|  |
| --- |
| Set-VBRVmBiosUuid -VCenterName "vcenter70" |


