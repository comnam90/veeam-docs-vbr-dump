---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_data_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore


In various disaster recovery scenarios, Veeam Backup & Replication allows you to perform the following restore operations using VM backups created by Veeam Plug-in for Universal Hypervisor API:

* [Restore of VMs](uh_restore_entire_vm.md) — start an entire VM from a restore point in the original location or a new location.

* [Restore of VM disks](uh_restore_disks.md) — restore specific VM disks and attach them to the original VM or to any other VM.

* [Instant Recovery](uh_restore_instant.md) —  immediately restore VMs directly from a backup to VMware, Hyper-V, Nutanix AHV and Proxmox VE environments.
* [Disk publishing](uh_disk_publish.md) — publish point-in-time disks, and copy the necessary files and folders to the target server.
* [File-level restore](uh_vm_guest_restore.md) — restore individual VM files and folders.

* [Application item restore](uh_restore_app_items.md) — restore applications such as Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint and Microsoft SQL Server.

* [VM disk export](uh_disk_export.md) — restore VM disks and convert them to disks in the VMDK, VHD or VHDX format.
* [Restore to AWS](uh_restore_to_amazon_ec2.md) — restore VMs to Amazon Web Services as EC2 instances.
* [Restore to Microsoft Azure](uh_restore_to_microsoft_azure.md) — restore VMs to Microsoft Azure as Azure VMs.
* [Restore to Google Cloud](uh_restore_to_google.md) — restore VMs to Google Cloud as VM instances.

You can restore VM data to the most recent state or to any available restore point.

Page updated 2026-07-06

