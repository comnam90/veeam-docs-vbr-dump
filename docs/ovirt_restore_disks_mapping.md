---
title: "Step 4. Configure Mapping Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_restore_disks_mapping.html"
last_updated: "1/28/2026"
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

|  |
| --- |
| Tip |
| You can instruct Veeam Plug-in for oVirt KVM to restore the disks in the QCOW2 format. This will [increase speed and efficiency of incremental backups](ovirt_changed_block_tracking.md) further created for the VM. |

![Step 4. Configure Mapping Settings](images/ovirt_restore_disk_mapping_change.webp "Disk Selection")


