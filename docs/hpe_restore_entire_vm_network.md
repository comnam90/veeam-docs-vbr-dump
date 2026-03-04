---
title: "Step 7. Configure Network Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_restore_entire_vm_network.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Step 7. Configure Network Settings


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Network step of the wizard, choose a network to which the recovered VM will be connected. For a network to be displayed in the list of available networks, it must be configured in the virtual environment as described in [HPE Morpheus VM Essentials documentation](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00007027en_us&page=GUID-451A0EAA-D2AF-4529-AEF0-9543A638CE03.html).

|  |
| --- |
| Note |
| Since HPE Morpheus VM Essentials requires all VMs to be connected to networks, you cannot choose the Disconnect option while restoring VMs. |

![Step 7. Configure Network Settings](images/hpe_restore_entire_vm_network.webp)


