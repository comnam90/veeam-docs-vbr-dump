---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_data_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore


In various disaster recovery scenarios, Veeam Plug-in for Nutanix AHV allows you to perform the following operations using backed-up data:

* [Restore of VMs](ahv_restore_to_ahv.md) — start an entire VM from a restore point in the original location or a new location..
* [Restore of VM disks](ahv_restore_disks.md) — restore specific VM disks and attach them to the original VM or to any other VM.
* [Instant Recovery](ahv_instant_recovery.md) — immediately restore VMs or VM disk directly from a backup to VMware, Hyper-V, Nutanix AHV and Proxmox VE environments.
* [Disk publishing](ahv_publish_disk.md) — publish point-in-time disks, and copy the necessary files and folders to the target server.
* [File-level restore](ahv_restoring_guest_os_files.md) — recover individual VM guest OS files and folders.
* [Application items restore](ahv_restore_app_items.md) — restore applications, such as Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint, and Microsoft SQL Server.
* [VM disk export](ahv_exporting_disk_content.md) — restore VM disks and convert them to disks of the VMDK, VHD or VHDX format.
* [Restore to AWS](ahv_restore_to_ec2.md) — restore Nutanix AHV VMs to Amazon Web Services as EC2 instances.
* [Restore to Microsoft Azure](ahv_restore_to_azure.md) — restore Nutanix AHV VMs to Microsoft Azure as Azure VMs.
* [Restore to Google Cloud](ahv_restore_to_google_ce.md) — restore Nutanix AHV VMs to Google Cloud as VM instances.

You can restore VM data to the most recent state or to any available restore point.

Page updated 2026-07-28

