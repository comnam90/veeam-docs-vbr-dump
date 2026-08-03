---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_instant_recovery_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you perform Instant Recovery, do the following:

* Power off the original machine if it is still present in the target location.
* Deploy a [dedicated server](mount_server.md) to mount workload images directly from backups stored in backup repositories and allocate minimum 512 MB of additional RAM for each VM disk that you want to recover. Make sure that the Server for NFS role and the Client for NFS component are not installed on the server, and that the [Veeam vPower NFS Service](vpower_nfs_service.md) is running.

* [Applies only to VMs being restored from backups stored in the archive tier of scale-out backup repositories] Retrieve backup data as described in section [Retrieving Backup Files](retrieval_job_launch.md). However, this requirement is not applicable to backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent.

* [Applies only to Linux VMs] Make sure that the file systems (also referred to as devices or partitions) listed in the /etc/fstab file are mounted using UUIDs. Instant Recovery of file systems mounted using device names is not supported as the restored VMs may fail to boot.

* [Applies only to Windows VMs being restored from backups created by solutions other than Veeam Plug-in for Proxmox VE] Make sure to install QEMU Guest Tools on the VMs — before the backups are created. You will not be able to add or modify the VM drivers during the recovery operation.

* [Applies only to VMs being restored from backups created by solutions other than Veeam Plug-in for Proxmox VE] Veeam Plug-in for Proxmox VE attaches VM disks with the restored data to the target VM disk nodes using their original bus types. Veeam Plug-in for Proxmox VE can attach to a VM up to 6 SATA, 31 SCSI, 4 IDE and 16 VIRTIO disks. If the VM has more disks of any of those bus types, Proxmox VE will attach the disks to remaining nodes of other bus types in the default priority: SATA, SCSI, IDE, VIRTIO. You can [modify the plug-in configuration](pve_bus_type_restore_order.md), to instruct Proxmox VE to ignore source VM original bus types and to use a specific order of bus types.

Page updated 2026-07-13

