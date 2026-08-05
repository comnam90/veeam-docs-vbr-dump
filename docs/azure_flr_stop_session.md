---
title: "Step 7. Stop Recovery Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_flr_stop_session.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 7. Stop Recovery Session


After you finish working with the file-level recovery browser, it is recommended that you stop the recovery session so that Veeam Backup for Microsoft Azure can unmount and detach virtual disks of the processed Azure VM from the worker instance and deallocate the worker instance.

To stop the recovery session, click Stop in the File-Level Recovery window. If you do not perform any actions in the file-level recovery browser for 30 minutes, and if no files are being restored, Veeam Backup for Microsoft Azure will stop the recovery session automatically.

|  |
| --- |
| Tip |
| If you accidentally close the File-Level Recovery window, navigate to Protected Data and click the link in the File-Level Recovery URL column to open the window again. |

[![Performing File-Level Recovery](images/azure_flr_stop.webp)](images/azure_flr_stop.webp "Performing File-Level Recovery")

Page updated 2025-04-07

