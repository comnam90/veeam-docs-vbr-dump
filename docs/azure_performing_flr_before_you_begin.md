---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_flr_before_you_begin.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you start file-level recovery, consider the following limitations and prerequisites:

* File-level recovery is supported from FAT, FAT32, NTFS, ext2, ext3, ext4, XFS, Btrfs file systems only. For Microsoft Windows systems, file-level recovery is supported for basic volumes only.
* If you want to recover files from file systems that are not supported by Veeam Backup for Microsoft Azure, you can add a backup repository that contains backups of Azure VMs to the backup infrastructure as an external repository, and perform the file-level recovery operation as described in [External Repositories](external_repository.md).
* File-level recovery to the original location is supported only for Windows-based Azure VMs running Windows Server version 2016 (or later) and Windows version 10 (or later), and for Linux-based Azure VMs using the [systemd init system](https://learn.microsoft.com/en-us/windows/wsl/systemd).
* File-level recovery of Azure VMs with the [Azure Disk Encryption option](https://learn.microsoft.com/en-us/azure/virtual-machines/disk-encryption-overview) enabled is not supported in the current Veeam Backup for Microsoft Azure version.
* File-level recovery from virtual disks with Windows-native [Data Deduplication](https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/overview) enabled is not supported. To work around the issue, you can restore entire virtual disks, and then attach these disks to an Azure VM with the deduplication feature enabled. To learn how to restore entire virtual disks, see [Performing Disk Restore](azure_performing_disk_restore.md).
* File-level recovery of [Arm-based Azure VMs](https://learn.microsoft.com/en-us/windows/arm/create-arm-vm) to the original location is not supported.
* To recover files and folders of an Azure VM from a backup that is stored in an archive backup repository, you must retrieve the archived data manually before you begin the file-level recovery operation. To learn how to do that, see [Retrieving Data from Archive](azure_retrieving_vm_data.md).

Page updated 2026-06-26

