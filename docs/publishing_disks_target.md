---
title: "Step 5. Specify Target Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/publishing_disks_target.html"
last_updated: "3/11/2025"
product_version: "13.0.1.1071"
---

# Step 5. Specify Target Server


At the Target step of the wizard, select a server that will have access to disk content — for Microsoft Windows file system a Microsoft Windows server; for Linux, Unix or other file system a Linux-based server. You can select one of the following types of servers:

* A server added to the backup infrastructure.
* A temporary server. In this case, select Specify a different host from the drop-down list. In the Target Server window, specify a server name or IP and credentials to the server.
* The original server if you publish disks from a backup created by Veeam Agent for Microsoft Windows or Veeam Agent for Linux. In this case, select Original server from the drop-down list.

If prompted, specify credentials for the target server.

![Step 5. Specify Target Server](images/disk_publish_target.webp)


