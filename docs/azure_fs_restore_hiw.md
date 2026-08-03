---
title: "Azure Files Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_fs_restore_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Azure Files Restore


To restore files and folders of an Azure file share, a backup appliance performs the following steps:

1. Mounts the source file share and the target file share on the backup appliance.
2. Launches the file-level recovery browser.

The file-level recovery browser displays the file tree of the backed-up file share. In the browser, you can specify the necessary restore point, and select files and folders that will be restored.

1. Restores the specified backed-up files and folders from the restore point to the selected file share.

To learn how to restore individual files and folders stored in a file system from an Azure Files backup, see [File Share Restore](azure_fs_restore.md).

Page updated 2026-07-01

