---
title: "Restoring Objects to Original Location"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vead_one_click_restore_objects.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Objects to Original Location


To restore an object to the original location, do the following:

1. In the preview pane, select objects.
2. On the Objects tab, select Restore Objects > Restore objects to <original\_location> or right-click an object and select Restore objects to <original\_location>.

Consider the following:

* Both changed and deleted objects will be restored.
* All the attributes will be restored.
* Attribute values and security descriptors will be replaced with that of a backup file.

|  |
| --- |
| Note |
| Before the restore process begins, you will be prompted to enter the source machine credentials. |

[![Restoring Objects](images/vead_1click_object_restore.webp)](images/vead_1click_object_restore.webp "Restoring Objects")

After the restore process is complete, review the results shown in the Restore Summary window. To do this, click See more to expand the window and review details of the restore operation.

You can filter notifications by their status: Error, Warning or Success.

![Restoring Objects to Original Location](images/restore_summary_objects.webp "Reviewing Restore Summary Window")

Page updated 2026-05-26

