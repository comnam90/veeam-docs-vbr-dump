---
title: "Step 7. Perform Post-Restore Operations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_restore_different_location_post.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Perform Post-Restore Operations


After the Restore session wizard completes the data transfer, perform the following steps on the target ODB server:

1. Stop the InterSystems IRIS instance.
2. (Optional) Set the correct file system permissions on the restored files using chmod, so that the InterSystems IRIS instance owner can access them.
3. Import the restored databases into the InterSystems IRIS instance to register the restored .DAT files. Use the InterSystems IRIS management portal or the command line to complete this step.
4. (Optional) Remove database files left over from the previous state of the target path that do not belong to the restored instance.
5. Start the InterSystems IRIS instance.

Page updated 2026-06-25

