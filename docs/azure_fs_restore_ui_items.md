---
title: "Step 7. Choose Items to Recover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_fs_restore_ui_items.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Choose Items to Recover


In the file-level recovery browser, you can find and restore items (files and folders) of the selected Azure file share. All restored items will be saved to the specified file share.

1. On the Browse tab, navigate to a folder that contains the necessary files.
2. In the working area, select check boxes next to the files and click Add to Restore List.
3. Repeat steps 1-2 for all other folders whose files you want to restore.
4. Switch to the Restore List tab, review the list of files and folders, select check boxes next to the items that you want to recover and do the following:

* To restore copies of the selected files and folders to the target file share, click Restore > Keep.

If files and folders with the same names exist on the target file share, the backup appliance will save the selected files to this file share with the following names — <file\_name>-Copy<ordinal\_number>. Otherwise, the backup appliance will save the selected files to this file share with the original names.

* To restore the selected files and folders to the target file share, click Restore > Overwrite.

If files and folders with the same names exist on the target file share, the backup appliance will overwrite these files. Otherwise, the backup appliance will save the selected files to this file share.

As soon as you click Restore, the backup appliance will recover the selected files. You can track the progress and view the results of the restore operation in the Session Log section of the Restore List tab.

[![Adding Files and Folders to Recovery List](images/azure_fs_adding_to_recovery_list.webp)](images/azure_fs_adding_to_recovery_list.webp "Adding Files and Folders to Recovery List")

Page updated 2026-07-01

