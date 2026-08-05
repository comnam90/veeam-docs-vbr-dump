---
title: "Step 6. Complete Restore Process"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_instant_restore_media_remote_complete.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Complete Restore Process


At the Summary step of the wizard, review the settings of the remote bare metal recovery. To copy the configuration to the clipboard for future reference, click Copy to Clipboard. Click Finish to start the restore.

During the restore, Veeam Backup & Replication transfers backup data to the recovery appliance, restores volumes according to the configured allocation, and injects drivers into the restored operating system. The restore session is saved with the type Restore Recovery Appliance Volumes.

After the restore finishes, reboot the recovery appliance to boot the computer into the restored operating system. To do this, in the Veeam Backup & Replication web UI, navigate to Bare Metal Recovery, select the recovery appliance and click Reboot on the toolbar.

![Step 6. Complete Restore Process](images/agent_restore_rbmr_complete.webp "Complete Restore Process")

Page updated 2026-07-21

