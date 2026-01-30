---
title: "Disk Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/disk_restores_hv.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# Disk Recovery


Veeam Backup & Replication does not provide platform-specific disk recovery methods. However,Veeam Backup & Replication provides the following platform-independent methods for disk recovery:

* [Disk export](disk_export.md) — to convert disks of different workloads (EC2 instances, Microsoft Azure VMs and so on) in the VMDK, VHD or VHDX formats. Then you can export these disks to the backup infrastructure or place them on a datastore connected to an ESXi host (for VMDK disk format only).

Use disk export to convert disks to the VMDK, VHD or VHDX formats.

* [Disk publishing](data_integration_api.md) — to get the backup content without restoring all disks from a backup. After you publish a disk, you can browse its content, perform antivirus scan and other testing.
* [Disk Restore to oVirt KVM](disk_restore_ovirt_kvm.md)\* — to recover different workloads as OLVM and RHV VM disks.

\* - Available on Microsoft Windows-based backup server.


