---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_data_recovery.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Performing Restore


In various disaster recovery scenarios, Veeam Plug-in for oVirt KVM allows you to perform the following operations using backed-up data:

* [Entire VM restore](ovirt_restore_to_rhv.md) — recover VMs to the original location or to a new location.

* [VM disk restore](ovirt_restore_disks.md) — recover a specific VM disk and attach it to the original VM or to another VM.
* [Instant VM recovery](ovirt_instant_vm_recovery.md) — instantly start a VM directly from a backup.
* [Disk publishing](ovirt_publish_disk.md) — mount specific disks of a backed-up VMs to any server added to the backup infrastructure.
* [File-level restore](ovirt_vm_guest_restore.md) — recover individual VM guest OS files and folders.
* [Application items restore](ovirt_application_items_restore.md) — restore applications, such as Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint, and Microsoft SQL Server.
* [VM disk export](ovirt_vm_disk_export.md) — restore VM disks and convert them to disks of the VMDK, VHD or VHDX format.
* [Performing VM Restore to Amazon Web Services](ovirt_restore_to_amazon_ec2.md) — restore VMs to Amazon Web Services as EC2 instances.
* [Performing VM Restore to Microsoft Azure](ovirt_restore_to_microsoft_azure.md) — restore VMs to Microsoft Azure as Azure VMs.
* [Performing VM Restore to Google Cloud](ovirt_restore_to_google_ce.md) — restore VMs to Google Cloud as VM instances.

You can restore VM data to the most recent state or to any available restore point.


