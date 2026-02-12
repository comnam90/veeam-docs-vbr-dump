---
title: "Performing File-Level Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_vm_guest_restore.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Performing File-Level Restore


With guest OS file recovery (file-level restore), you can restore individual guest OS files and folders from VM backups created with Veeam Plug-in for Scale Computing HyperCore. When restoring files and folders, you do not need to extract the VM image to a staging location or start the VM prior to restore. For more information on VM guest OS file restore, see section [Guest OS File Recovery](guest_file_recovery.md).

To restore VM guest OS files and folders, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, expand the necessary backup job, right-click the VM that contains files you want to restore and select Restore guest files.

Alternatively, you can select the VM and click Restore Guest Files on the ribbon.

1. Complete the File Level Restore wizard as described in section [Recovering Guest OS Files Using Console](performing_guest_restore.md).

|  |
| --- |
| Note |
| To restore files of a VM with an operation system other than Microsoft Windows, Veeam Plug-in for Scale Computing HyperCore requires a [mount host](guest_file_recovery.md) — a server that will be used to mount VM disks. While completing the Guest File Restore wizard, you will be able either to choose a server already added to the backup infrastructure or to specify connection settings of a new server that will be used as a mount host.  If you want to select temporary helper appliance as a mount host option, you can deploy it only on a VMware vSphere, Microsoft Hyper-V or Nutanix AHV machine.  For file-level restore to work, Veeam Plug-in for Scale Computing HyperCore must be able to obtain source VM IP address which requires guest tools to be installed on the VM. |

[![VM Guest OS Files Restore](images/sch_vm_guest_restore.webp)](images/sch_vm_guest_restore.webp "VM Guest OS Files Restore")


