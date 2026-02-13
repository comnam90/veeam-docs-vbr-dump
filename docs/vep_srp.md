---
title: "Step 2. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_srp.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Point


At this step of the wizard, select a state as of which you want to publish your data.

1. Choose a point-in-time state.

* Select the Restore to the point in time of the selected image-level backup option to load instance files as of the moment when the current restore point was created.
* Select the Restore to a specific point in time option to obtain instance files as of the selected point in time within the available restore period. Use the slider to choose the point in time you need.

Note that if the backed-up WAL files do not contain information about some instances for the selected point in time, those instances will be recovered as of their latest available state.

1. Click Publish.

![Step 2. Specify Restore Point](images/vep_publish_pit_state_restore_point.webp "Specifying Restore Point")


