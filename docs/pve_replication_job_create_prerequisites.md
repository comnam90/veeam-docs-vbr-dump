---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_replication_job_create_prerequisites.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you create a replication job, consider the following limitations:

* You can replicate each VM with one replication job at a time. If a VM is already being processed by a replication job, another replication job will not start processing this VM until the currently running replication operation completes.
* You cannot replicate a VM being restored. Wait for the restore process to complete, and then start the replication job.
* You cannot replicate VMs with the same BIOS UUID.
* You cannot include into a replication job a VM that is being processed by 3rd party software. Wait for the process to complete or stop the currently running job manually, and then add the VM to the necessary replication job.
* You cannot include into a replication job a resource pool that does not contain any VMs. Note that after you update a resource pool in the Proxmox VE administration portal, it may take up to 15 minutes for Veeam Plug-in for Proxmox VE to synchronize data between Proxmox VE and Veeam Backup & Replication.
* Veeam Plug-in for Proxmox VE does not support replication of iSCSI disks. If iSCSI disks are attached to a VM included into a replication job, these disks will be skipped from processing.
* If the original VM is missing disks that exist on the replica VM, Veeam Plug-in for Proxmox VE will automatically create the missing disks during failback. The missing disks will be placed on the Proxmox VE storage that supports VM disk creation and has the most available free space.
* A replication job may fail if the source VM has disks whose size is not a multiple of the target storage block size.

Page updated 2026-07-27

