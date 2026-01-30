---
title: "Disk Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/disk_restores.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# Disk Recovery


Disk recovery includes the following methods for the VMware vSphere platform:

* [Instant Disk Recovery](instant_disk_recovery.md) — to instantly recover VM disks from backup files. The disks are recovered in their initial format.

Instant Disk Recovery helps improve recovery time objectives (RTO) but publishes disks with the reduced I/O performance, that is, provides “temporary spares”. To provide the full I/O performance, you must finalize Instant Disk Recovery — migrate the recovered disks to the production environment. If you do not want to migrate the recovered disks, you can stop publishing them. This removes the recovered disks.

Use Instant Disk Recovery if you want to keep the target VM (VM to which you want to attach recovered disks) turned on. If the VM can be turned off, you can use virtual disk restore.

* [Instant First Class Disk Recovery](instant_disk_recovery_fcd.md) — to instantly recover VM disks from backup files and register them as First Class Disks (FCDs). FCDs are a type of improved VMDK that allow you to perform different tasks: create snapshots, delete and restore data stored on VMDK without attaching these disks to a VM.

This method is similar to Instant Disk Recovery except for the format in which disks are recovered.

Use Instant FCD Recovery if you want to recover recovered disks as FCDs.

* [Virtual disk restore](virtual_drive_recovery.md) — to restore VM disks. When you restore disks, you extract them from backups to the production storage. Virtual disk restore takes more resources to complete than Instant Disk Recovery but restores disks with full I/O performance. You also do not need to perform additional steps to finalize the restore process.

Use virtual disk restore if the target VM can be turned off. If the VM must stay turned on, perform Instant Disk Recovery.

Veeam Backup & Replication provides the following platform-independent methods for disk recovery:

* [Disk export](disk_export.md) — to convert disks of different workloads (EC2 instances, Microsoft Azure VMs and so on) in the VMDK, VHD or VHDX formats. Then you can export these disks to the backup infrastructure or place them on a datastore connected to an ESXi host (for VMDK disk format only).

Use disk export to convert disks to the VMDK, VHD or VHDX formats.

* [Disk publishing](data_integration_api.md) — to get the backup content without restoring all disks from a backup. After you publish a disk, you can browse its content, perform antivirus scan and other testing.
* [Disk Restore to oVirt KVM](disk_restore_ovirt_kvm.md)\* — to recover different workloads as OLVM and RHV VM disks.

\* - Available on Microsoft Windows-based backup server.


