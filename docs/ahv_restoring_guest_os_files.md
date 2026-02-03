---
title: "Performing File-Level Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restoring_guest_os_files.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Performing File-Level Restore


With guest OS file recovery (file-level restore), you can restore individual guest OS files and folders from Nutanix AHV VM snapshots and backups created with Veeam Plug-in for Nutanix AHV. When restoring files and folders, you do not need to extract the VM image to a staging location or start the VM prior to restore.

|  |
| --- |
| Note |
| Veeam Plug-in for Nutanix AHV does not support restore from Novell Storage Service (NSS) file systems. |

To restore VM guest OS files and folders, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, expand the necessary backup job, right-click the VM that contains files you want to restore and select Restore guest files.

Alternatively, expand the necessary backup job, select the VM click Restore Guest Files on the ribbon.

|  |
| --- |
| Tip |
| To restore VM guest OS files and folders from a backup snapshot, expand the job that contains the snapshot of the VM, right-click the VM and select Restore guest files. |

1. Complete the File Level Restore wizard as described in section [Recovering Guest OS Files Using Console](performing_guest_restore.md).

|  |
| --- |
| Note |
| Depending on the operating system of a VM whose files and folders you want to restore, Veeam Backup & Replication may require a [mount server](guest_file_recovery.md) — a server that will be used to mount VM disks. While completing the File Level Restore wizard, you will be able either to choose a server already added to the backup infrastructure or to specify connection settings of a new server that will used as the mount server. For more information on how Veeam Backup & Replication selects mount servers, see [Mount Server Automatic Selection](guest_restore_scenarios.md). |

[![Performing File-Level Restore](images/ahv_restore_guest_os_files.webp)](images/ahv_restore_guest_os_files.webp)

|  |
| --- |
| Tip |
| Alternatively, you can use Veeam Backup Enterprise Manager to restore guest OS files and folders as described in the Veeam Backup Enterprise Manager Guide, section [Restoring VM Guest OS Files](https://helpcenter.veeam.com/docs/vbr/em/searching_restoring_vm_guest_files.html?ver=13). |


