---
title: "VM Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_restores_hv.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# VM Recovery


VM recovery includes the following methods for the Microsoft Hyper-V platform:

* [Entire VM restore](full_recovery_hv.md) — to recover entire VMs. When you recover VMs, you extract VM images from backups to the production storage. Entire VM restore takes more resources and time to complete than Instant Recovery but recovers VMs with full I/O performance. You also do not need to perform additional steps to finalize the recovery process.

Use entire VM restore for VMs that require full I/O performance as soon as they are recovered and that tolerate some downtime.

* [Staged restore](staged_restore_about_hv.md) — to run executable scripts for VMs before recovering them to the production environment. Staged restore is a part of entire VM restore.

Use this option when you need to make sure that recovered VMs do not contain any personal or sensitive data.

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


