---
title: "Step 4. Finalize Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/guest_restore_save_vm_web.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Step 4. Finalize Recovery


You can recover files and folders to the original location, download files to the machine where the web UI is opened and review which files were recovered.

Restoring Files to Original Location

To recover files and folders to the original location:

1. Select the necessary files and folders in the working area.
2. Right-click one of the selected items and select one of the following:

* To save the restored files and folders next to the original ones, select Restore > Keep.

Veeam Backup & Replication will add the RESTORED\_YYYYMMDD\_HHMMSS postfix to the original names and store the restored items in the same folder where the original items reside.

* To overwrite the original files and folders with the ones restored from the backup, select Restore > Overwrite.

Alternatively, you can select the same commands on the ribbon.

[![Restore to Original Location - Web UI](images/guest_restore_save_origin_vm_web.webp)](images/guest_restore_save_origin_vm_web.webp "Restore to Original Location - Web UI")

Downloading Files

To download files and folders to a machine where the Veeam Backup & Replication web UI is opened, select files and folders in the working area. Right-click one of the selected items and click Download. Veeam Backup & Replication will start downloading a .ZIP file.

[![Download Files - Web UI](images/guest_restore_save_vm_web.webp)](images/guest_restore_save_vm_web.webp "Download Files - Web UI")

Viewing Recovered Files

To view the list of files that were recovered, navigate to the Audit tab on the top bar.

[![See Audit Information - Web UI](images/guest_restore_save_audit_web.webp)](images/guest_restore_save_audit_web.webp "See Audit Information - Web UI")


