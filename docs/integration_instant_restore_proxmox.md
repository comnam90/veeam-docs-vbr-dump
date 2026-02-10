---
title: "Restoring Veeam Agent Backup to Proxmox VM"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_instant_restore_proxmox.html"
last_updated: "2/9/2026"
product_version: "13.0.1.1071"
---

# Restoring Veeam Agent Backup to Proxmox VM


You can use the Veeam Backup & Replication console to restore a Veeam Agent computer as a Proxmox VE VM in your virtualization environment.

Considerations and Limitations

If you restore a Veeam Agent computer to a Proxmox VE VM, consider the following:

* You can use backups of Microsoft Windows and Linux computers stored in a Veeam backup repository only. You cannot perform this operation with Veeam Agent backups stored in a Veeam Cloud Connect repository.
* [For backups of Linux computers]If the disk you want to restore contains a Logical Volume Manager (LVM) volume group, consider the following:

* Since LVM volume group is a logical entity that spans across the physical disks, Veeam Agent treats the original disk and the LVM volume group as separate entities. Therefore, Veeam Agent will restore the original disk and the LVM volume group as 2 separate disks. This way, all data, including the data within the LVM volume group, is accurately restored.
* Restoring the original disk and the LVM volume groups as 2 separate disks requires an increased amount of storage space. For example, you restore a machine with 2 disks, and a separate LVM volume group is configured on each of these disks. In this case, Veeam Agent will restore 4 disks. The restored disks will consume the storage space equal to the size of the 2 original disks and the 2 LVM volume groups from these disks.

|  |
| --- |
| TIP |
| After restore, you can remove unnecessary disks from the machine. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4680). |

Restore to Proxmox VE

The procedure of restore to Proxmox VE for a Veeam Agent computer practically does not differ from the same procedure for a VM. To learn more about restore to Proxmox VE, see the [Performing VM Restore](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/restore_entire_vm.html?ver=1) section in the Veeam Backup for Proxmox VE User Guide.

[![Restore Veeam Agent Backup to Proxmox VE](images/am_agent_restore_proxmox.webp)](images/am_agent_restore_proxmox.webp "Restore Veeam Agent Backup to Proxmox VE")


