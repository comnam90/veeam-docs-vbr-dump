---
title: "Step 2. Select File Share to Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_entire_file_share_backup.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Step 2. Select File Share to Restore


At the File Shares step of the wizard, select the file share that you want to restore:

1. Click Add.
2. In the Backups Browser window, select the file backup job and a file share in it that you want to restore. Click OK.
3. In the File shares table, choose the file share to select a restore point to restore to. Click Point.
4. In the Select Restore Point window, select the restore point to which you want to restore the file share. To select the required restore point, do one of the following:

* Use the Restore point slider.
* Click the date link under the Restore point slider. In the calendar in the left pane of the Select Restore Point window, select the date when the required restore point was created. The list of restore points in the right pane displays restore points created on the selected date. Select the point to which you want to restore the file share.

In the Files in backup tree, you can see what folders and files are covered by the selected restore point and the date when each of them was modified.

Click OK.

To quickly find a file share, you can use the search field at the top of the window. Enter a file share name or a part of it in the search field and press [Enter].

To exclude the file share from the restore process, select the file share in the table and click Remove.

![Step 2. Select File Share to Restore](images/nas_file_restore_backup.webp "Select an Object to Restore")


