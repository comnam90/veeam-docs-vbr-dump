---
title: "Step 6. Perform Post-Restore Operations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_restore_snapshot_original_location_post.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Perform Post-Restore Operations


After the restore wizard completes a restore from storage snapshot, perform the following manual steps on the ODB server:

1. Stop the InterSystems IRIS instance.
2. Unmount the production disks and remove LUN masking.
3. (Optional) Convert the snapshot clones from thin to thick provisioning.
4. Start the InterSystems IRIS instance.

Page updated 2026-06-25

