---
title: "Step 8. Finalize Instant Application Backup Repository Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_abr_recovery_finalize.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 8. Finalize Instant Application Backup Repository Recovery


This step of the wizard is available if you selected the Export snapshot via temporary path option at the Restore Mode step of the wizard.

After the repository data has been exported to a temporary NFS share, you must finalize the recovery process. For this, access the temporary NFS share using the mount path you provided at the Destination step of the wizard to browse the data.

When the data recovery is done, and the snapshot export can be stopped, you can stop publishing the exported data. This will dismount the temporary NFS share that you specified as the destination for recovery. Note that all changes made in the temporary NFS folder during the recovery process will be lost.

To stop exporting the application backup repository snapshot:

1. Open the Home view.
2. In the inventory pane, select the Instant Recovery node.
3. In the working area, right-click the application backup repository host and select Stop publishing. Alternatively, you can click Stop Publishing on the ribbon.

[![Step 8. Finalize Instant Application Backup Repository Recovery](images/instant_abr_recovery_finalize.webp)](images/instant_abr_recovery_finalize.webp)

Page updated 2026-06-23

