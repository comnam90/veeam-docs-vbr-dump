---
title: "Step 11. Verify Recovery Settings and Finish Working with Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_full_vm_restore_verify.html"
last_updated: "11/19/2024"
product_version: "13.0.1.1071"
---

# Step 11. Verify Recovery Settings and Finish Working with Wizard


At the Summary step of the wizard, specify additional settings for VMs restore:

1. If you want to start the restored VMs, select the Power on VM after restoring check box.
2. Check the settings for VMs restore and click Finish. Veeam Backup & Replication will recover the VMs in the specified destination.

|  |
| --- |
| Note |
| Veeam Backup & Replication checks the lease term for the restored VMs. In case the lease period has expired, the lease will be automatically updated. |

![Step 11. Verify Recovery Settings and Finish Working with Wizard](images/vcloud_full_restore_finish.webp)


