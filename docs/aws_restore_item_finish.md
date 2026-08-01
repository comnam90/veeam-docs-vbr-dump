---
title: "Step 5. Start Recovery Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_item_finish.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Start Recovery Session


At the Summary step of the wizard, review summary information and click Finish.

As soon as you click Finish, the backup appliance will close the File-level Recovery wizard, start a recovery session and display the FLR Running Sessions window. During the recovery session, the backup appliance will deploy a worker instance and attach EBS volumes of the processed EC2 instance to it.

|  |
| --- |
| Tip |
| If you accidentally close the FLR Running Sessions window, navigate to Protected Data > EC2 and click the link in the File-Level Recovery URL column to open the window again. |

In the FLR Running Sessions window you can track the progress of the recovery session. As soon as worker instance is deployed, the backup appliance will display a link to the file-level recovery browser in the URL column of the window. You can use the link in either of the following ways:

* Click the link to open the file-level recovery browser on your local machine while the recovery session is running.
* Copy the link, close the FLR Running Sessions window and open the file-level recovery browser on another machine.

|  |
| --- |
| Important |
| When you click Copy URL, the backup appliance copies the following information to the clipboard:   * A link to the file-level recovery browser includes a public DNS name or private IP address of the worker instance hosting the browser and authentication information used to access the browser. * A thumbprint of a TLS certificate installed on the worker instance hosting the file-level recovery browser.   To avoid a man-in-the-middle attack, before you start recovering files and folders, check that the certificate thumbprint displayed in the web browser from which you access the file-level recovery browser matches the provided certificate thumbprint. |

[![Restoring EC2 Files and Folders](images/aws_restore_item_flr_session_view.webp)](images/aws_restore_item_flr_session_view.webp "Restoring EC2 Files and Folders")

Page updated 2026-05-22

