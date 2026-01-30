---
title: "Step 11. Verify Recovery Settings and Finish Working with Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_vapp_restore_verify.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Step 11. Verify Recovery Settings and Finish Working with Wizard


At the Summary step of the wizard, specify additional settings for vApp restore:

1. If you want to start VMs in the restored vApp, select the Power on VM after restoring check box.
2. Check the settings for vApp restore and click Finish. Veeam Backup & Replication will recover the vApp in the specified destination.

|  |
| --- |
| Note |
| Veeam Backup & Replication checks the lease term for the restored vApp. If the lease period has expired, the lease will be automatically updated. |

![Step 11. Verify Recovery Settings and Finish Working with Wizard](images/vcloud_restore_finish.webp)


