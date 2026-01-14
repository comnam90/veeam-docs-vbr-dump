---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replica_limitations_hv.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

Replication has the following requirements and limitations:

* The target host version must be equal or later than the source host version. However, you can fail back from the source 2016 host to the target 2012 R2 host if a VM replica configuration version is lower than 8.0.
* The target VM configuration version must be equal or higher than the source VM configuration version.

* [For VMs with VHD disks] If you change the size of VM disks on the source VM, Veeam Backup & Replication will delete all available restore points on the VM replica during the next replication job session.
* [For VMs with VHDX disks] If you change the size of VM disks on the source VM, Veeam Backup & Replication resets [changed block tracking (CBT)](changed_block_tracking_hv.md).
* Veeam Backup & Replication does not support protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).
* Disks that were deleted from the source VM configuration are not automatically deleted from the target Hyper-V host storage.
* [Off-host replication scenario](replication_scenarios_hv.md) is possible for VMs located on a SAN storage with a hardware VSS provider and for VMs located on an SMB share with a VSS provider.
* Replication of VMs with disabled checkpoints is not supported.
* You cannot replicate VMs with shared VHDX and VHDS disks.
* Due to Microsoft limitations, you cannot use Microsoft Entra ID (formerly Azure Active Directory) credentials to perform application-aware processing on VMs running Microsoft Windows 10 (or later).
* If a job is unable to complete within 21 days period, it will be stopped with the Failed status.

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
