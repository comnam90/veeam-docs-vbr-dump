---
title: "Step 3. Select Files and Folders to Be Copied"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_copy_source.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Step 3. Select Files and Folders to Be Copied


At the Source step of the wizard, select the files and folders you want to copy.

To select files and folders:

1. Click Add to open the Specify Folder window.
2. From the Server list, choose a host or server where the files or folders reside.
3. Select the files or folders you want to copy. The selected items will be added to the list.

|  |
| --- |
| Important |
| If the list contains files or folders with the same names and extensions, Veeam Backup & Replication copies only one instance of the file or folder. This limitation applies even if you add files or folders from different hosts or servers. To avoid this limitation, you can rename files or folders on the source, or add parent folders to the list. |

To remove a file or folder from the list, select it and click Remove.

![Step 3. Select Files and Folders to Be Copied](images/file_copy_source_vm.webp)


