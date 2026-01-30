---
title: "Restoring Disk from Veeam Agent Backup to oVirt KVM"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_restore_ovirt_disk.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Restoring Disk from Veeam Agent Backup to oVirt KVM


You can use the Veeam Backup & Replication console to restore disks from a Veeam Agent computer backup to an oVirt KVM VM in your virtualization environment.

Considerations and Limitations

If you restore disks to an oVirt KVM VM, consider the following:

* You can use backups of Microsoft Windows and Linux computers stored in a Veeam backup repository only. You cannot perform this operation with Veeam Agent backups stored in a Veeam Cloud Connect repository.
* [For backups of Linux computers]If the disk you want to restore contains a Logical Volume Manager (LVM) volume group, consider the following:

* Since LVM volume group is a logical entity that spans across the physical disks, Veeam Agent treats the original disk and the LVM volume group as separate entities. Therefore, Veeam Agent will restore the original disk and the LVM volume group as 2 separate disks. This way, all data, including the data within the LVM volume group, is accurately restored.
* Restoring the original disk and the LVM volume groups as 2 separate disks requires an increased amount of storage space. For example, you restore a machine with 2 disks, and a separate LVM volume group is configured on each of these disks. In this case, Veeam Agent will restore 4 disks. The restored disks will consume the storage space equal to the size of the 2 original disks and the 2 LVM volume groups from these disks.

|  |
| --- |
| TIP |
| After restore, you can remove unnecessary disks from the machine. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4680). |

Restore to oVirt KVM VM

The procedure of restoring disks to an oVirt KVM VM for a Veeam Agent computer practically does not differ from the same procedure for a VM. To learn more, see the [Performing Disk Restore](https://helpcenter.veeam.com/docs/vbrhv/userguide/restore_disks.html?ver=6) section in the Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization User Guide.

[![Restore Disk from Veeam Agent Backup to oVirt KVM](images/am_agent_restore_ovirt_disks.webp)](images/am_agent_restore_ovirt_disks.webp "Restore Disk from Veeam Agent Backup to oVirt KVM")


