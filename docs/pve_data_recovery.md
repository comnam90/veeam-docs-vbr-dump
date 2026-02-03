---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_data_recovery.html"
last_updated: "6/30/2025"
product_version: "13.0.1.1071"
---

# Performing Restore


In various disaster recovery scenarios, Veeam Backup & Replication allows you to perform the following operations using backed-up data:

* [Entire VM restore](pve_restore_entire_vm.md) — recover Proxmox VE VMs to the original location or to a new location.

* [Instant VM recovery](pve_restore_instant.md) — instantly start an Proxmox VE VM directly from a backup.
* [Disk publishing](pve_disk_publish.md) — mount specific disks of a backed-up Proxmox VE VMs to any server added to the backup infrastructure.
* [File-level restore](pve_vm_guest_restore.md) — recover individual VM guest OS files and folders.

* [Application items restore](pve_restore_app_items.md) — restore applications, such as Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint, and Microsoft SQL Server.

* [VM disk export](pve_disk_export.md) — restore VM disks and convert them to disks of the VMDK, VHD or VHDX format.
* [VM restore to Amazon Web Services](pve_restore_to_amazon_ec2.md) — restore Proxmox VE VMs to Amazon Web Services as EC2 instances.
* [VM restore to Microsoft Azure](pve_restore_to_microsoft_azure.md) — restore Proxmox VE VMs to Microsoft Azure as Azure VMs.
* [VM restore to Google Cloud](pve_restore_to_google.md) — restore Proxmox VE VMs to Google Cloud as VM instances.

You can restore VM data to the most recent state or to any available restore point.


