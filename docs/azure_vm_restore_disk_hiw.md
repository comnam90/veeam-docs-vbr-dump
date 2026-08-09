---
title: "Disk Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_restore_disk_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Disk Restore


In case a disaster strikes, you can restore corrupted virtual disks of an Azure VM from a cloud-native snapshot or image-level backup. Veeam Backup for Microsoft Azure allows you to restore virtual disks to the original location or to a new location.

How Disk Restore Works

To restore virtual disks from a cloud-native snapshot, backup appliances use [native Microsoft Azure capabilities](https://docs.microsoft.com/en-us/azure/backup/backup-azure-arm-restore-vms). To restore virtual disks from an image-level backup, a backup appliance performs the following steps:

1. [Applies only if you perform restore from an archived backup] Retrieves data from the archived restore point.
2. [Applies only if you perform restore to the original location] Creates a staging resource group in which virtual disks of the restored Azure VM will be created, and assigns the Veeam backup appliance ID tag to the group. The tag value is the ID of Azure VM running the backup appliance.
3. Creates empty virtual disks. The number of empty virtual disks equals the number of disks you want to restore.
4. Launches a worker instance in the Azure region where the restored virtual disks will reside, and attaches the empty virtual disks to the worker instance.
5. Restores backed-up data to the empty virtual disks on the worker instance.
6. Detaches the virtual disks with the restored data from the worker instance.
7. Deallocates the worker instance.
8. [Applies only if you perform restore to the original location] Removes the source virtual disks from Microsoft Azure.
9. [Applies only if you perform restore to the original location] Moves the virtual disks from the staging resource group to the original resource group.
10. [Applies only if you perform restore to the original location] Attaches the created virtual disks with the restored data to the Azure VM.
11. [Applies only if you perform restore to the original location] Removes the staging resource group.

|  |
| --- |
| Note |
| When restoring to a new location, the backup appliance does not attach the restored virtual disks to any Azure VM — the disks are placed to the specified location as standalone virtual disks. |

To learn how to restore virtual disks attached to an Azure VM from a cloud-native snapshot or an image-level backup, see [Performing Disk Restore](azure_performing_disk_restore.md).

Page updated 2026-07-01

