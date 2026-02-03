---
title: "Performing Instant Recovery of Workloads to Nutanix AHV"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_instant_recovery_ahv.html"
last_updated: "1/12/2026"
product_version: "13.0.1.1071"
---

# Performing Instant Recovery of Workloads to Nutanix AHV


You can immediately restore virtual or physical machines into a Nutanix AHV cluster by running it directly from a compressed and deduplicated backup file. Before you perform Instant Recovery, check the following prerequisites:

* The cluster runs Nutanix AOS 6.0 or later.
* The cluster is [added to the backup infrastructure](ahv_add_ahv_cluster.md).

Supported Workloads

To recover machines to a Nutanix AHV cluster, you can use the following backups:

* Backups of Nutanix AHV VMs created by Veeam Plug-in for Nutanix AHV

* Backups of Microsoft Hyper-V and VMware vSphere VMs created by Veeam Backup & Replication

* Backups of virtual and physical machines created by Veeam Agent for Microsoft Windows and Veeam Agent for Linux
* Backups of VMs created by vCloud Director
* Backups of Amazon EC2 instances created by Veeam Backup for AWS

* Backups of Microsoft Azure VMs created by Veeam Backup for Microsoft Azure
* Backups of Google Cloud VMs instances created by Veeam Backup for Google Cloud
* Backups of oVirt KVM VMs created by Veeam Plug-in for Oracle Linux Virtualization Manager and Red Hat Virtualization

* Backups of Proxmox VE VMs created by Veeam Plug-in for Proxmox VE

Instant Recovery is not supported:

* From backups of VMs with the ARM CPU architecture
* From file-level backups created by Kasten 10, Veeam Agent for Linux, Veeam Agent for Microsoft Windows, Veeam Agent for Unix, Veeam Agent for Mac

|  |
| --- |
| Note |
| Instant Recovery to Nutanix AHV is supported only for backups stored in backup repositories, object storage repositories, external repositories, [Veeam Cloud Connect repositories](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13), [HPE Cloud Bank Storage](storeonce_supported_features.md) and a scale-out backup repository (performance, capacity or archive tier). Instant Recovery from backups stored on tapes is not supported. |

How Instant Recovery Works

When Instant Recovery is performed, Veeam Plug-in for Nutanix AHV mounts a workload image to a [mount server](mount_server.md) directly from a compressed and deduplicated backup file. Since there is no need to extract the workload from the backup file and copy it to production storage, you can perform recovery from any restore point in a matter of minutes.

The workload image remains in the read-only state to avoid unexpected modifications. By default, all changes to virtual disks that take place while the recovered workload is running are logged to auxiliary redo log files residing in the cluster. These changes are either merged if you choose to migrate the workload to the production environment, or discarded if you choose to revert the recovery operation.

How to Perform Instant Recovery to AHV

To perform Instant Recovery of a protected workload, do the following:

1. [Check prerequisites and limitations](ahv_byb_instant_recovery_ahv.md).
2. [Launch the Instant Recovery wizard](ahv_ir_launch_ahv.md).
3. [Choose a restore point](ahv_ir_workloads_ahv.md).
4. [Choose a restore mode](ahv_ir_mode_ahv.md).
5. [Select a target cluster](ahv_ir_target_cluster_ahv.md).
6. [Select a target storage container](ahv_ir_target_container_ahv.md).
7. [Specify a name for the restored workload](ahv_ir_vm_name_ahv.md).
8. [Configure network settings](ahv_ir_network_ahv.md).
9. [Specify a restore reason](ahv_ir_reason_ahv.md).
10. [Review the configured settings](ahv_ir_verify_ahv.md).
11. [Finalize the recovery process](ahv_ir_finalize_ahv.md).


