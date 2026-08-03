---
title: "Viewing Backup Properties"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/view_backup_properties.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Viewing Backup Properties


You can view summary information about created backups. The summary information provides the following data:

* Available restore points.
* Date of restore points creation.
* Data reduction ratio.
* Data size (amount of data before data reduction), backup size (actual, physical amount of data stored in the repository after data reduction), original size (size of the selected VM) and total size (sum of the original sizes of all objects).
* GFS retention policy applied to restore points (W — weekly; M — monthly; Y — yearly).
* Backup retention date. This column is available for backups created by [VeeamZIP](veeamzip.md), [export backup](exporting_backups.md) or [copy backup](copy_backup.md) and with the retention period specified.

In the Backup Properties window, you can see different icons whose meaning is described in the [Infrastructure Icons](infrastructure_icons.md#restore_points) section.

To view summary information for backups:

1. Open the Home view.
2. In the [inventory pane](vbr_ui.md), select Backups.
3. In the working area, right-click the backup and select Properties.
4. To see the list of available restore points, select the required object in the left pane.
5. To display only the restore points that have issues, select the Show issues only check box.

[![Viewing Backup Properties](images/view_backup_properties.webp)](images/view_backup_properties.webp)

Page updated 2026-07-29

