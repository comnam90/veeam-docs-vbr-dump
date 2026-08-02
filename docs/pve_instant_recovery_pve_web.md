---
title: "Performing Instant Recovery of Workloads to Proxmox VE"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_instant_recovery_pve_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Instant Recovery of Workloads to Proxmox VE


You can immediately restore virtual or physical machines into a Proxmox VE host by running it directly from a compressed and deduplicated backup file. You can perform Instant Recovery directly from the [Veeam Backup & Replication web UI](web_ui_logon.md). Before you perform Instant Recovery, check the following prerequisites:

* The cluster runs Proxmox Virtual Environment versions 8.2–9 or later.
* The cluster is [added to the backup infrastructure](pve_server_add.md).

Supported Workloads

To recover machines to a Veeam Plug-in for Proxmox VE host, you can use the following backups:

* Backups of Proxmox VE VMs created by Veeam Plug-in for Proxmox VE
* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV
* Backups of oVirt VMs created by Veeam Plug-in for oVirt KVM
* Backups of HPE Morpheus VM Essentials VMs created by Veeam Plug-in for HPE Morpheus VM Essentials
* Backups of Sangfor aSV VMs created by Veeam Plug-in for Sangfor aSV
* Backups of Scale Computing HyperCore VMs created by Veeam Plug-in for Scale Computing HyperCore
* Backups of VMs created by universal hypervisor
* Backups of Xen and XCP-ng VMs created by Veeam Plug-in for Xen
* Backups of VMs residing on universal hypervisors created by Veeam Plug-in for Universal Hypervisor API
* Backups of Microsoft Hyper-V and VMware vSphere VMs created by Veeam Backup & Replication
* Backups of virtual and physical machines created by Veeam Agent for Microsoft Windows and Veeam Agent for Linux
* Backups of VMware Cloud Director VMs created by Veeam Backup & Replication
* Backups of Amazon EC2 instances created by Veeam Plug-in for AWS
* Backups of Microsoft Azure VMs created by Veeam Plug-in for Microsoft Azure
* Backups of Google Cloud VM instances created by Veeam Plug-in for Google Cloud

Instant Recovery is not supported:

* From backups of VMs with the ARM CPU architecture
* From file-level backups created by Kasten 10, Veeam Agent for Linux, Veeam Agent for Microsoft Windows, Veeam Agent for Unix, Veeam Agent for Mac

|  |
| --- |
| Note |
| Instant Recovery to Proxmox VE is supported only for backups stored in backup repositories, object storage repositories, external repositories, [Veeam Cloud Connect repositories](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13), [HPE Cloud Bank Storage](storeonce_supported_features.md) and a scale-out backup repository (performance, capacity or archive tier). Instant Recovery from backups stored on tapes is not supported. |

How Instant Recovery Works

When Instant Recovery is performed, Veeam Plug-in for Proxmox VE mounts a workload image to a [mount server](mount_server.md) directly from a compressed and deduplicated backup file. Since there is no need to extract the workload from the backup file and copy it to production storage, you can perform recovery from any restore point in a matter of minutes.

The workload image remains in the read-only state to avoid unexpected modifications. By default, all changes to virtual disks that take place while the recovered workload is running are logged to auxiliary redo log files residing on the host. These changes are either merged if you choose to migrate the workload to the production environment, or discarded if you choose to revert the recovery operation.

How to Perform Instant Recovery

To perform Instant Recovery of a protected workload, do the following:

1. [Check prerequisites and limitations](pve_instant_recovery_byb_web.md).
2. [Launch the Instant Recovery wizard](pve_instant_recovery_launch_web.md).
3. [Choose a restore point](pve_instant_recovery_vms_web.md).
4. [Choose a restore mode](pve_instant_recovery_mode_web.md).
5. [Specify a target host](pve_instant_recovery_target_host_web.md).
6. [Specify a name for the restored VM](pve_instant_recovery_vm_name_web.md).
7. [Select storage](pve_instant_recovery_target_storage_web.md).
8. [Configure network settings](pve_instant_recovery_network_web.md).
9. [Specify a restore reason](pve_instant_recovery_reason_web.md).
10. [Review the configured settings](pve_instant_recovery_summary_web.md).
11. [Finalize the recovery process](pve_instant_recovery_finalize_web.md).

Page updated 2026-07-27

