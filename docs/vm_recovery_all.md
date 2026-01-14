---
title: "VM Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_recovery_all.html"
last_updated: "12/12/2025"
product_version: "13.0.1.1071"
---

# VM Recovery

In this article

Platform-independent VM recovery includes the following methods:

* [Instant Recovery to VMware vSphere](instant_recovery.md) — to instantly recover workloads (VMs, EC2 instances, physical servers and so on) directly from compressed and deduplicated backup files as VMware vSphere VMs. When you perform Instant Recovery, Veeam Backup & Replication mounts recovered VM images to a host directly from backups stored on backup repositories.

Instant Recovery helps improve recovery time objectives (RTO), minimize disruption and downtime of production workloads. However, Instant Recovery provides for VMs “temporary spares” with limited I/O performance. To provide the recovered VMs full I/O performance, you must finalize Instant Recovery — migrate the recovered VMs to production environment. If you do not want to migrate the recovered VM, you can stop publishing it. This removes the recovered VM.

Use Instant Recovery for tier 1 VMs with little tolerance for business interruption and downtime. Besides disaster recovery matters, Instant Recovery can also be used for testing purposes.

* [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md) — to instantly recover workloads directly from compressed and deduplicated backup files as Microsoft Hyper-V VMs. In many respects, this method is similar to Instant Recovery to VMware vSphere.
* [Instant Recovery to Microsoft Azure](instant_recovery_to_azure.md) — to instantly recover workloads directly from compressed and deduplicated backup files as Microsoft Azure VMs.
* [Instant Recovery to Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/instant_recovery_ahv.html?ver=9) — to instantly recover workloads directly from compressed and deduplicated backup files as Nutanix AHV VMs.
* [Restore to Amazon EC2](restore_amazon.md) — to restore workloads of different data protection environments as EC2 instances.
* [Restore to Microsoft Azure](restore_azure.md) — to restore workloads of different data protection environments as Microsoft Azure VMs.
* [Restore to Google Compute Engine (GCE)](restore_google.md) — to restore workloads of different data protection environments as Google VM instances.
* [Restore to Nutanix AHV](restore_ahv.md) — to restore workloads of different data protection environments as Nutanix AHV VMs.
* [Restore to Proxmox VE](restore_prox.md) — to restore workloads of different data protection environments as Proxmox VE VMs.
* [Restore to OLVM and RHV\*](restore_olvm_rhv.md) — to restore workloads of different data protection environments as OLVM and RHV VMs.

\* - Available on Microsoft Windows-based backup server.

Veeam Backup & Replication also provides platform-independent methods. For more information, see the Data Recovery section for the necessary platform.

Related Topics

* [Data Recovery (VMware vSphere)](data_recovery.md)
* [Data Recovery (VMware Cloud Director)](vcloud_director_vm_restore.md)
* [Data Recovery (Microsoft Hyper-V)](data_recovery_hv.md)
* [Unstructured Data Recovery](unstructured_data_recovery.md)
* [VM Restore from Tape to Infrastructure](vm_restore_from_tape.md)

Page updated 12/12/2025

Page content applies to build 13.0.1.1071
