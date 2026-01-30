---
title: "VM Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_vm_restore.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# VM Recovery


VMware Cloud Director VM recovery includes the following methods:

* Instant Recovery to Cloud Director vApp — to instantly recover Cloud Director VMs directly from compressed and deduplicated backup files to vApps. Instant Recovery helps improve recovery time objectives (RTO), minimize disruption and downtime of production workloads. However, Instant Recovery provides for VMs “temporary spares” with limited I/O performance. To provide the recovered VMs full I/O performance, you must finalize Instant Recovery — migrate the recovered VMs to production environment. If you do not want to migrate the recovered VM, you can stop publishing it. This removes the recovered VM.

For more information, see [Performing Instant Recovery to Cloud Director vApp](vcloud_director_instant_vm_restore_to_vcd.md).

* Restore of VMs to Cloud Director vApp — to recover entire VMs to vApps. When you recover VMs, you extract VM images from backups to the production storage. This restore takes more resources and time to complete than Instant Recovery to Cloud Director vApp but recovers VMs with full I/O performance. You also do not need to perform additional steps to finalize the recovery process.

For more information, see [Restoring Entire VMs into Cloud Director vApp](vcloud_director_full_vm_restore.md).

* Entire VM restore to VMware vSphere  — to restore VMware Cloud Director VMs from the backup to the VMware vSphere infrastructure.

During restore, Veeam Backup & Replication neglects the vApp metadata saved to the backup file and performs a regular entire VM restore process. The VM is restored to the vCenter Server or ESXi host and is not registered in VMware Cloud Director. Cloud Director-specific features such as fast provisioning are not supported for such type of restore.

Veeam Backup & Replication provides the following platform-independent methods for workload recovery:

* [Instant Recovery to VMware vSphere](instant_recovery.md) — to instantly recover workloads (VMs, EC2 instances, physical servers and so on) directly from compressed and deduplicated backup files as VMware vSphere VMs. When you perform Instant Recovery, Veeam Backup & Replication mounts recovered VM images to a host directly from backups stored on backup repositories.

Instant Recovery helps improve recovery time objectives (RTO), minimize disruption and downtime of production workloads. However, Instant Recovery provides for VMs “temporary spares” with limited I/O performance. To provide the recovered VMs full I/O performance, you must finalize Instant Recovery — migrate the recovered VMs to production environment. If you do not want to migrate the recovered VM, you can stop publishing it. This removes the recovered VM.

Use Instant Recovery for tier 1 VMs with little tolerance for business interruption and downtime. Besides disaster recovery matters, Instant Recovery can also be used for testing purposes.

* [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md) — to instantly recover workloads directly from compressed and deduplicated backup files as Microsoft Hyper-V VMs. In many respects, this method is similar to Instant Recovery to VMware vSphere.

* [Instant Recovery to Microsoft Azure](instant_recovery_to_azure.md) — to instantly recover workloads directly from compressed and deduplicated backup files as Microsoft Azure VMs.

* [Instant Recovery to Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/instant_recovery_ahv.html?ver=9) — to instantly recover workloads directly from compressed and deduplicated backup files as Nutanix AHV VMs. Note that to restore to Nutanix AHV, you must install Nutanix AHV Plug-in on the backup server. For more information, see the [Installation](https://helpcenter.veeam.com/docs/vbahv/userguide/install_ahv_services.html?ver=9) section in the Veeam Plug-In for Nutanix AHV User Guide.
* [Restore to Amazon EC2](restore_amazon.md) — to restore workloads of different data protection environments as EC2 instances.
* [Restore to Microsoft Azure](restore_azure.md) — to restore workloads of different data protection environments as Microsoft Azure VMs.
* [Restore to Google Compute Engine (GCE)](restore_google.md) — to restore workloads of different data protection environments as Google VM instances.
* [Restore to Nutanix AHV](restore_ahv.md) — to restore workloads of different data protection environments as Nutanix AHV VMs.
* [Restore to Proxmox VE](restore_prox.md) — to restore workloads of different data protection environments as Proxmox VE VMs.
* [Restore to OLVM and RHV](restore_olvm_rhv.md)\* — to restore workloads of different data protection environments as OLVM and RHV VMs.

\* - Available on Microsoft Windows-based backup server.


