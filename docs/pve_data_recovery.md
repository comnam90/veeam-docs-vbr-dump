---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_data_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore


In various disaster recovery scenarios, Veeam Backup & Replication allows you to perform the following restore operations using VM backups created by Veeam Plug-in for Proxmox VE:

* [Restore of VMs](pve_restore_entire_vm.md) — start an entire VM from a restore point in the original location or a new location.

* [Instant Recovery](pve_restore_instant.md) — immediately restore VMs directly from a backup to VMware, Hyper-V, Nutanix AHV and Proxmox VE environments.
* [Disk publishing](pve_disk_publish.md) — publish point-in-time disks, and copy the necessary files and folders to the target server.
* [File-level restore](pve_vm_guest_restore.md) — restore individual VM files and folders.

* [Application item restore](pve_restore_app_items.md) — restore applications such as Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint and Microsoft SQL Server.

* [VM disk export](pve_disk_export.md) — restore VM disks and convert them to disks in the VMDK, VHD or VHDX format.
* [Restore to AWS](pve_restore_to_amazon_ec2.md) — restore VMs to Amazon Web Services as EC2 instances.
* [Restore to Microsoft Azure](pve_restore_to_microsoft_azure.md) — restore VMs to Microsoft Azure as Azure VMs.
* [Restore to Google Cloud](pve_restore_to_google.md) — restore VMs to Google Cloud as VM instances.

You can restore VM data to the most recent state or to any available restore point.

Page updated 2026-07-20

