---
title: "Step 5. Specify Database Files Location"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_export_specify_file_location.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Database Files Location


At this step of the wizard, specify the location to which data files will be restored.

Consider the following:

* When restoring with the Restore with the original name and settings option, only the location for Data files will be available for editing.
* When restoring with the Restore with different name and settings option, the location for the following files will be available for editing:

* Data files
* Log files
* Temp files

|  |
| --- |
| Note |
| Even though the Control files paths are available for editing at this step, the edits will not be applied in the generated recovery script. |

To change the target location, click the row and specify the path.

![Step 5. Specify Database Files Location](images/rman_export_specify_file_location.webp "Specifying Database Files Target Location")

Page updated 2026-07-16

