---
title: "FSx Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_fsx.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# FSx Restore


|  |
| --- |
| Important |
| You can restore an FSx file system only to the same AWS account to which the source file system belongs. |

To restore an FSx file system from a backup, a backup appliance performs the following steps using native AWS capabilities:

1. Creates a file system in the specified location.
2. Modifies the configuration setting values of the created FSx file system.
3. Restores backed-up files and folders to the restored file system.

To learn how to restore an Amazon FSx file system from an FSx backup or a backup copy, see [FSx Restore](aws_fsx_restore.md).

Page updated 2026-05-15

