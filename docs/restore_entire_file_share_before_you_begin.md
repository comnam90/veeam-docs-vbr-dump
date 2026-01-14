---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_entire_file_share_before_you_begin.html"
last_updated: "5/15/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you restore the entire file share, consider the following:

* You can restore files and folders of the file share from a backup that has at least one successfully created restore point.
* The file share on which you plan to save restored files and folders must be added to the backup infrastructure.
* During the backup of an SMB file share, Veeam Backup & Replication does not collect ACL for the root shared folder. Therefore, if you restore the entire file share, ACL of the root folder is not restored. To solve this issue, prepare a folder with the required permissions before running the entire file share restore. During the restore, use this folder as a target root folder for the restored share.
* Regardless of restore options, if a backup has an item with the same name but a different type as one in the file share, this file will not be restored. For example, folder named test.txt and a text file named text.

Page updated 5/15/2024

Page content applies to build 13.0.1.1071
