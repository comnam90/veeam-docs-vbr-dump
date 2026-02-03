---
title: "Step 3. Choose Restore Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_ir_mode_ahv.html"
last_updated: "1/28/2026"
product_version: "13.0.1.1071"
---

# Step 3. Choose Restore Mode


[This step applies only if you restore Nutanix AHV VMs]

At the Restore Mode step of the wizard, choose whether you want to restore the selected VM to the original or to a custom location.

To meet minimum requirements for VMs residing on a cluster, Veeam Plug-in for Nutanix AHV allocates 64 MB of RAM to the recovered VM if it originally had less amount of memory.

|  |
| --- |
| Important |
| If you recover a VM with original settings, and the original VM still exists in the virtual infrastructure, the original VM will be removed. |

![Step 3. Choose Restore Mode](images/ahv_ir_mode_ahv.webp)


