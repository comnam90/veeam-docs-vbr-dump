---
title: "Platform-Independent Data Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_recovery_all_vm.html"
last_updated: "12/10/2025"
product_version: "13.0.1.1071"
---

# Platform-Independent Data Recovery


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

Veeam Backup & Replication provides the following platform-independent methods for disk recovery:

* [Disk export](disk_export.md) — to convert disks of different workloads (EC2 instances, Microsoft Azure VMs and so on) in the VMDK, VHD or VHDX formats. Then you can export these disks to the backup infrastructure or place them on a datastore connected to an ESXi host (for VMDK disk format only).

Use disk export to convert disks to the VMDK, VHD or VHDX formats.

* [Disk publishing](data_integration_api.md) — to get the backup content without restoring all disks from a backup. After you publish a disk, you can browse its content, perform antivirus scan and other testing.
* [Disk Restore to oVirt KVM](disk_restore_ovirt_kvm.md)\* — to recover different workloads as OLVM and RHV VM disks.

\* - Available on Microsoft Windows-based backup server.

Veeam Backup & Replication provides the following platform-independent methods for item recovery:

* [Guest OS file restore](guest_file_recovery.md) — to restore individual guest OS files from Windows, Linux, Mac and other guest OS file systems. You can restore files and folders directly from a regular image-level backup, storage snapshot or replica.
* [Application items restore](restore_veeam_explorers.md) — to restore items from different applications such as Microsoft Active Directory, Microsoft SQL Server and so on. Application items are recovered directly from VM backups and replicas. To recover application items, Veeam Backup & Replication uses the capabilities of Veeam Explorers.

For more information, see [Data Recovery (All Platforms)](data_recovery_all.md).


