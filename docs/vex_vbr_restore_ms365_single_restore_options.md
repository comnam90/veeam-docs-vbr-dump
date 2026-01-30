---
title: "Step 8. Specify Restore Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vex_vbr_restore_ms365_single_restore_options.html"
last_updated: "9/19/2024"
product_version: "13.0.1.1071"
---

# Step 8. Specify Restore Options


At this step of the wizard, select restore options and click Restore.

You can select the following options:

* Changed items

Select this check box if you want to restore items that have been changed. When you select this option, Veeam Explorer for Microsoft Exchange overwrites existing items in your target location.

* Missing Items

Select this check box if you want to restore items that are missing in your target location. For example, some of the items were removed and you want to restore them from the backup.

* Mark restored items as unread

Select this check box if you want to mark each restored item as unread.

If you restore a mailbox, to prevent certain folders from being restored, click the Exclude folders link and select folders to exclude.

|  |
| --- |
| Note |
| The Exclude folders link is not available when restoring folders and items. |

[![Specify Restore Options](images/vex_restore_options.webp)](images/vex_restore_options.webp "Specify Restore Options")


