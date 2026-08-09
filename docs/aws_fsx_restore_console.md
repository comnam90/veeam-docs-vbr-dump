---
title: "FSx Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_fsx_restore_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# FSx Restore Using Console


You can recover corrupted FSx file systems in the backup appliance Web UI only. However, you can launch the FSx Restore wizard directly from the Veeam Backup & Replication console to start the restore operation:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > Snapshots.
3. Expand the backup policy that protects the FSx file systems you want to recover, select the necessary file system and click Amazon FSx on the ribbon.

Alternatively, you can right-click the selected file system and click Restore to Amazon FSx.

|  |
| --- |
| Important |
| You cannot restore multiple FSx file systems from the Veeam Backup & Replication console. |

Veeam Backup & Replication will open the FSx Restore wizard in a web browser. Complete the wizard as described in section [FSx Restore Using Web UI](aws_restore_point_fsx.md).

[![Restore to Amazon FSx](images/aws_restore_fsx.webp)](images/aws_restore_fsx.webp "Restore to Amazon FSx")

Page updated 2026-07-20

