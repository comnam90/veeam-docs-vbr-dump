---
title: "Disk Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/disk_recovery_all.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# Disk Recovery

In this article

Platform-independent disk recovery includes the following methods:

* [Disk export](disk_export.md) — to convert disks of different workloads (EC2 instances, Microsoft Azure VMs and so on) in the VMDK, VHD or VHDX formats. Then you can export these disks to the backup infrastructure or place them on a datastore connected to a host (for VMDK disk format only).

Use disk export to convert disks to the VMDK, VHD or VHDX formats.

* [Disk publishing](data_integration_api.md) — to get the backup content without restoring all disks from a backup. After you publish a disk, you can browse its content, perform antivirus scan and other testing.
* [Disk Restore to oVirt KVM](disk_restore_ovirt_kvm.md) — to recover different workloads as OLVM and RHV VM disks. This recovery method is available on the Microsoft Windows-based backup server.

Veeam Backup & Replication also provides platform-independent methods. For more information, see the Data Recovery section for the necessary platform.

Related Topics

* [Data Recovery (VMware vSphere)](data_recovery.md)
* [Data Recovery (VMware Cloud Director)](vcloud_director_vm_restore.md)
* [Data Recovery (Microsoft Hyper-V)](data_recovery_hv.md)
* [Unstructured Data Recovery](unstructured_data_recovery.md)
* [VM Restore from Tape to Infrastructure](vm_restore_from_tape.md)

Page updated 10/22/2025

Page content applies to build 13.0.1.1071
