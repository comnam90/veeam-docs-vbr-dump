---
title: "Step 4. Configure Mapping Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_disks_mapping.html"
last_updated: "1/27/2026"
product_version: "13.0.1.1071"
---

# Step 4. Configure Mapping Settings


At the Disk Mapping step of the wizard, do the following:

1. Choose a target VM to which you want to attach the restored disks.

By default, Veeam Backup & Replication attaches the restored disks to the original VM. To attach the disks to another VM, click Choose.

|  |
| --- |
| Important |
| During disk restore, Veeam Backup & Replication turns off the target VM to reconfigure its settings and attach the restored disks. It is recommended that you stop all activities on the target VM till the restore session completes. |

1. Select virtual disks to restore.

By default, Veeam Backup & Replication attaches the restored disks to the target VM as new disks. If you want the restored disks to replace the existing disks, or if you want to change the disk bus type and to specify a storage domain for the restored disks, click Change.

![Step 4. Configure Mapping Settings](images/ahv_restore_disk_mapping.webp "Configure Mapping Settings")


