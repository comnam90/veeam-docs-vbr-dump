---
title: "Restoring Guest OS Files"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/guest_file_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Guest OS Files


You can restore individual guest OS files and folders from backups exported from Veeam Kasten. You can restore files and folders directly from image-level backups. For more information, see the [Guest OS File Restore](https://helpcenter.veeam.com/docs/vbr/userguide/guest_file_recovery.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| Consider the following:   * Veeam Plug-in for Kasten supports only restore from Linux, Unix and other non-Microsoft Windows OSes. * Veeam Plug-in for Kasten does not support restore of individual guest OS files and folders to the original location (applications added to a Veeam Kasten cluster). You can only save files and folders to a new location. For more information, see the [Saving Files to New Location](https://helpcenter.veeam.com/docs/backup/vsphere/multios_restore_save_vm.html?ver=120#restoring-files-and-folders-to-new-location) section in the Veeam Backup & Replication User Guide. |

To restore guest OS files from Linux, Unix and other file systems, do the following:

1. Check [considerations and limitations](https://helpcenter.veeam.com/docs/vbr/userguide/vbr_flr_considerations_common.html?ver=13) listed in the Veeam Backup & Replication User Guide.
2. Launch and complete the File Level Restore wizard. To do that, open the Home view and navigate to Backups > Disk. In the working area, select an application whose files you want to restore. On the ribbon, click Restore Guest Files. Alternatively, right-click the application and select Restore guest files.
3. Complete the wizard as described in the [Recovering Guest OS Files Using Console](https://helpcenter.veeam.com/docs/vbr/userguide/performing_guest_restore.html?ver=13) section in the Veeam Backup & Replication User Guide.

[![Restore Guest OS](images/guest_os.webp)](images/guest_os.webp "Restore Guest OS")

Page updated 2026-07-09

