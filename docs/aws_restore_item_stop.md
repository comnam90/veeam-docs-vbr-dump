---
title: "Step 7. Stop Recovery Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_item_stop.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Stop Recovery Session


After you finish working with the file-level recovery browser, it is recommended that you stop the recovery session so that the backup appliance can unmount and detach EBS volumes of the processed EC2 instance from the worker instance and remove the worker instance from Amazon EC2.

To stop the recovery session, click Stop recovery session in the FLR Running Sessions window. If you do not perform any actions in the file-level recovery browser for 30 minutes, the backup appliance will stop the recovery session automatically.

|  |
| --- |
| Tip |
| If you accidentally close the FLR Running Sessions window, navigate to Protected Data > EC2 and click the link in the File-Level Recovery URL column to open the window again. |

[![Restoring EC2 Files and Folders](images/aws_restore_item_flr_session_stop.webp)](images/aws_restore_item_flr_session_stop.webp "Restoring EC2 Files and Folders")

Page updated 2026-05-22

