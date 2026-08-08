---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_how_vm_backup_works.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VM Backup


A backup appliance performs VM backup in the following way:

1. The backup appliance creates snapshots of virtual disks that are attached to the processed Azure VM.

Disk snapshots are assigned Azure tags upon creation. Values of Azure tags contain encrypted metadata that helps the backup appliance identify the related disk snapshots and treat them as a single unit — a cloud-native snapshot. For this reason, you must not delete any Azure tags whose names start with the word veeam.

|  |
| --- |
| Important |
| Due to Microsoft Azure limitations, you can apply up to 50 tags directly to a subscription. That is why Veeam Backup for Microsoft Azure is able to create a snapshot only if the tag limit is not reached for the subscription to which the processed Azure VM belongs. If the limit is reached, the operation will fail with a serialization error. For more information on subscription limits, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#subscription-limits). |

1. If you enable image-level backup for the backup policy, the backup appliance performs the following operations:

1. Launches a worker instance in an Azure region in which the processed Azure VM resides.

By default, the backup appliance launches worker instances using virtual networks created automatically. However, you can add specific worker configurations. For more information, see [Managing Worker Instances](azure_worker_configurations.md).

1. Reads data from the created cloud-native snapshot using a [shared access signature (SAS) URI](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview), compresses the data and transfers it to the target repository, and stores it in the native Veeam format.

To reduce the amount of data read from snapshots, the backup appliance uses the changed block tracking (CBT) mechanism: during incremental backup sessions, the backup appliance compares the new cloud-native snapshot with the previous one and reads only those data blocks that have changed since the previous backup session. For more information, see [Changed Block Tracking](azure_changed_block_tracking.md).

|  |
| --- |
| Note |
| The backup appliance encrypts and compresses data saved to repositories. For more information on data encryption, see [Data Encryption](azure_data_encryption.md). |

1. Deallocates the worker instance when the backup session completes.

1. If you enable the [backup archiving mechanism](azure_vm_backup_archiving.md), the backup appliance performs the following operations:

1. Launches a worker instance in an Azure region in which the target repository resides.
2. Retrieves data from the repository and transfers it to the target archive repository.
3. Deallocates the worker instance when the archive session completes.

|  |
| --- |
| Note |
| Veeam Backup for Microsoft Azure stores the backed-up data depending on the type of the virtual disk attached to the protected Azure VM:   * Snapshots created for managed virtual disks are saved to the same Azure region and resource group to which the Azure VM belongs. * Snapshots created for unmanaged virtual disks are saved to the same Azure storage account where these disks reside. * Backups created for managed and unmanaged virtual disks are saved to the target repository.   For more information on Azure virtual disk types, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/managed-disks-overview). |

Related Topics

* [Snapshot Chain](azure_snapshot_chain_vm.md)
* [Backup Chain](azure_backup_chain_vm.md)
* [VM Backup Retention](azure_vm_backup_retention.md)

Page updated 2026-07-01

