---
title: "Step 6. Finalize Instant Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_recovery_disks_summary.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Finalize Instant Recovery


At the Summary step of the wizard, review summary information and click Finish.

|  |
| --- |
| Tip |
| If you want to start the VM with recovered disks as soon as the restore process completes, select the Power on VM after restore check box. |

To finalize the instant recovery operation, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the inventory pane, select Instant Recovery.
3. In the working area, right-click the VM:

* To transfer VM disk data to the production storage, select Migrate to production.
* To remove the recovered disks, select Stop publishing.

|  |
| --- |
| Important |
| If you stop publishing a VM that was recovered to the same destination where the original VM resided, both the original and recovered VMs will be removed. |

[![Step 4. Specify VM Name](images/ahv_recovery_disk_summary.webp)](images/ahv_recovery_disk_summary.webp "Step 4. Specify VM Name")

Page updated 2026-07-16

