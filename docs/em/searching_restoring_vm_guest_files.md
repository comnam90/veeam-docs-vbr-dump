---
title: "Guest OS File Restore"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/searching_restoring_vm_guest_files.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Guest OS File Restore


Veeam Backup Enterprise Manager allows you to browse the guest OS file system in a machine backup, search for guest OS files and restore the necessary files. You can locate and restore files from the machine restore point created with or without guest OS file indexing.

Before you start recovering your files, consider the following:

* Browsing and restoring processes involve appropriate backup job setup, as well as file system mounting and data transfer operations. For details, see [Preparing for File Browsing and Searching](preparing_for_file_browsing.md).

* Veeam Backup Enterprise Manager lets you browse and recover guest OS files from backups of Proxmox VE, Nutanix AHV and oVirt KVM (Oracle Linux Virtualization Manager and Red Hat Virtualization) machines. The following operations are supported:

* For Proxmox VE and oVirt KVM, you can browse files and download them to the local machine.
* For Nutanix AHV VMs, you can browse files, download them to the local machine, and restore them to the original location.

* To browse and restore guest OS files and application items from a physical machine backup stored in a Veeam backup repository, you need a certain Veeam Agent deployed on the machine and integrated with Veeam Backup & Replication. For more information, see [Veeam Agents Support](em_support_physical.md).

* Enterprise Manager does not support 1-Click restore, 1-Click guest OS file restore, or application item-level restore for Microsoft Exchange mailbox items or Microsoft SQL Server databases if it is performed from any storage snapshot.

How File Restore Works

When you restore files from the restore point created with guest OS file indexing enabled, Veeam Backup & Replication uses the following workflow:

1. To provide for browsing and search, Veeam Backup Enterprise Manager uses index data to represent the file system of the machine guest OS.
2. If you then select to download the necessary files, Veeam Backup & Replication will mount machine disks (from the restore point) on the backup server and copy these files from the backup server to the destination location.
3. If you select to restore files to the original location, an additional mount point will be created on the mount server associated with the backup repository storing the backup file. During restore, machine data will flow from the repository to the target, keeping the machine traffic in one site and reducing load on the network.
4. After you download or restore the necessary files, and finish the restore session, the machine disks will be unmounted.

When you restore files from the restore point that was created without machine guest OS file indexing, Veeam Backup & Replication uses the following workflow:

1. To provide for browsing, disks of the machine from the backup file are mounted to the backup server. If you then select to download the necessary files, Veeam Backup & Replication will copy these files from the backup server to the destination location, using this mount point.
2. If you select to restore files from the backup to the original location on the production machine, an additional mount point will be created on the mount server associated with the backup repository storing the backup file.
3. If you restore files from replica, a single mount point for all these operations (browsing, download, restore to original location) will be created on the backup server.
4. After you download and restore the necessary files and finish the restore session, machine disks will be unmounted.

In This Section

* [Preparing for File Browsing and Searching](preparing_for_file_browsing.md)
* [Browsing Machine Backups for Guest OS Files](browsing_vm_backups.md)
* [Searching for Guest OS Files in Machine Backups](searching_vm_backups.md)
* [Performing 1-Click File Restore](performing_1-click_file_restore.md)
* [Restoring Files to Another Location](flr_another_location.md)
* [Using Self-Service File Restore Portal to Restore Machine Guest Files](em_self_restore.md)


