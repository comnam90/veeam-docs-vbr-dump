---
title: "Step 4. Specify Restore Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_vbr_restore_items_specify_restore_options.html"
last_updated: "3/19/2026"
product_version: "13.0.2.29"
---

# Step 4. Specify Restore Options


At this step of the wizard, select check boxes next to the restore options that you want to apply and click Restore.

You can select the following options:

* Changed items. Allows you to restore data that has been modified in your production environment.
* Missing items. Allows you to restore missing items.

* Restore only latest version. Allows you to restore only the latest version of items. If this check box is selected, you can select one of the following options:

* Merge. To merge an existing and a backup version of items.
* Overwrite. To overwrite data in the production environment.

If the Restore only latest version check box is not selected, backed-up versions of items will be merged with the existing versions in the production environment.

* Restore list views. Allows you to restore your list views.
* Restore subsites. Allows you to restore your subsites.

![Step 4. Specify Restore Options](images/specify_restore_options_2.webp "Specify Restore Options ")


