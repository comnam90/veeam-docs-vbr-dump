---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_data_recovery.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# Performing Restore


In various disaster recovery scenarios, Veeam Plug-in for Nutanix AHV allows you to perform the following operations using backed-up data:

* [Entire VM restore](ahv_restore_to_ahv.md) — recover Nutanix AHV VMs to the original location or to a new location.

* [VM disk restore](ahv_restore_disks.md) — recover a specific VM disk and attach it to the original VM or to another VM.
* [Instant VM recovery](ahv_instant_recovery.md) — instantly start a VM directly from a backup.

* [Disk publishing](ahv_publish_disk.md) — mount specific disks of a backed-up Nutanix AHV VMs to any server added to the backup infrastructure.

* [File-level restore](ahv_restoring_guest_os_files.md) — recover individual VM guest OS files and folders.

* [Application items restore](ahv_restore_app_items.md) — restore applications, such as Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint, and Microsoft SQL Server.

* [VM disk export](ahv_exporting_disk_content.md) — restore VM disks and convert them to disks of the VMDK, VHD or VHDX format.
* [Restore to AWS](ahv_restore_to_ec2.md) — restore Nutanix AHV VMs to Amazon Web Services as EC2 instances.
* [Restore to Microsoft Azure](ahv_restore_to_azure.md) — restore Nutanix AHV VMs to Microsoft Azure as Azure VMs.
* [Restore to Google Cloud](ahv_restore_to_google_ce.md) — restore Nutanix AHV VMs to Google Cloud as VM instances.


