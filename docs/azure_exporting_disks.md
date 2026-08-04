---
title: "Exporting Disks"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_exporting_disks.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Exporting Disks


Veeam Backup & Replication allows you to export disks, that is, to restore virtual disks of Azure VMs from image-level backups created by Veeam Backup for Microsoft Azure and to convert them to the VMDK, VHD and VHDX formats. You can save the converted disks to any server added to the backup infrastructure or place the disks on a datastore connected to an ESXi host (for the VMDK disk format only). For more information, see [Disk Export](disk_export.md).

|  |
| --- |
| Important |
| Disk export cannot be performed using backups that are stored in [Veeam Data Cloud storage vaults](azure_vdc_vaults.md). To perform this operation, use backups that are stored in standard backup repositories for which you have specified Microsoft Azure storage account credentials. To learn how to specify credentials for repositories, see sections [Creating New Repositories](azure_repository_console_storage_account.md) and [Connecting to Existing Appliances](azure_adding_appliance_repository.md). |

To restore disks of an Azure VM to the VMDK, VHD or VHDX format, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > External Repository.
3. Expand the backup policy that protects an Azure VM whose disks you want to restore, select the necessary VM and click Export Disk on the ribbon.
4. Complete the Export Disk wizard as described in [Exporting Disks](disk_export_machine.md).

[![Export disks](images/azure_export_disks.webp)](images/azure_export_disks.webp "Export disks")

Page updated 2026-06-26

