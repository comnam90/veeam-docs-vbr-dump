---
title: "Step 10. Finalize Instant Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_ir_finalize_ahv.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Step 10. Finalize Instant Recovery


After the VM has been recovered, you can choose whether you want to migrate the VM to the production environment or cancel the recovery operation. When migrating VMs, Veeam Plug-in for Nutanix AHV transfers VM disk data to the production storage that you have selected as a destination for the recovered VM.

To finalize the instant recovery operation, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the inventory pane, select Instant Recovery.
3. In the working area, right-click the VM:

* To transfer VM disk data to the production storage, select Migrate to production.
* To remove the recovered VM, select Stop publishing.

|  |
| --- |
| Important |
| If you stop publishing a VM that was recovered to the same destination where the original VM resided, both the original and recovered VMs will be removed. |

[![Finalize Instant Recovery](images/ahv_ir_finalize.webp)](images/ahv_ir_finalize.webp "Finalize Instant Recovery")


