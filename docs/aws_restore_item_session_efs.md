---
title: "Step 8. Open FLR Browser"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_item_session_efs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 8. Open FLR Browser


[This step applies only if you have selected the Browse files option at the Restore Type step of the wizard]

|  |
| --- |
| Tip |
| If you accidentally close the FLR Running Sessions window, navigate to Protected Data > File Systems > EFS and click the link in the File-Level Recovery URL column to open the window again. |

In the FLR Running Sessions window you can track the progress of the recovery session. In the URL column of the window, the backup appliance will display a link to the file-level recovery browser. You can use the link in either of the following ways:

* Click the link to open the file-level recovery browser on your local machine while the recovery session is running.
* Copy the link, close the FLR Running Sessions window and open the file-level recovery browser on another machine.

|  |
| --- |
| Important |
| When you click Copy URL, the backup appliance copies the following information to the clipboard:   * A link to the file-level recovery browser includes a public DNS name or an IP address of the backup appliance hosting the browser and authentication information used to access the browser. * A thumbprint of a TLS certificate installed on the appliance hosting the file-level recovery browser.   To avoid a man-in-the-middle attack, before you start recovering files and folders, check that the certificate thumbprint displayed in the web browser from which you access the file-level recovery browser matches the provided certificate thumbprint. |

[![Restoring EFS Files and Folders](images/aws_restore_item_flr_session_view_efs.webp)](images/aws_restore_item_flr_session_view_efs.webp "Restoring EFS Files and Folders")

Page updated 2026-05-22

