---
title: "Restore from Capacity Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_capacity_tier.html"
last_updated: "1/7/2026"
product_version: "13.0.1.1071"
---

# Restore from Capacity Tier


You can restore your data directly from the capacity tier back to production servers or to Microsoft Azure, Amazon EC2 or Google Cloud platforms. Capacity tier data recovery does not differ from that of a standard backup data recovery and can be performed by using any of the following methods:

* [Instant Recovery to VMware vSphere](instant_recovery.md)
* [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md)
* [Entire VM Restore](full_recovery.md)
* [VM Files Restore](vmfile_recovery.md)
* [For VMware vSphere] [Virtual Disk Restore](virtual_drive_recovery.md)
* [Guest OS File Restore](guest_file_recovery.md)
* [For VMware vSphere] [Instant Disk Recovery](instant_disk_recovery.md)
* [Disk Export](disk_export.md)
* [Application Item Restore from Image-Based Backups](restore_veeam_explorers.md)
* [Exporting Backups](exporting_backups.md)

Data recovery can also be done directly to Amazon EC2, Microsoft Azure or Google as described in sections [Restore to Amazon EC2](restore_amazon.md), [Restore to Microsoft Azure](restore_azure.md) and [Restore to Google Compute Engine](restore_google.md).

|  |
| --- |
| Note |
| To increase the speed of restore to Microsoft Azure, make sure that the following requirements are met:   * To restore data, use [Azure restore proxy appliances](restore_azure_proxy.md). * Azure restore proxy appliances must be located in the same Azure region, where you keep backups and Azure VMs created from backups. |

Related Topics

* [Restore Scenarios](capacity_tier_copy_rs.md)
* [Indexes](capacity_tier_indexing.md)
* [Managing Capacity Tier](managing_capacity_tier_data.md)


