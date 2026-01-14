---
title: "Instant Recovery to VMware vSphere"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Instant Recovery to VMware vSphere

In this article

With Instant Recovery to VMware vSphere, you can immediately recover different workloads (VMs, EC2 instances, physical servers and so on) as VMware vSphere VMs. Instant Recovery to VMware vSphere can be helpful, for example, if you want to migrate your infrastructure from one environment to another, or you want to recover your infrastructure in a matter of minutes but with limited performance.

During recovery, Veeam Backup & Replication runs workloads directly from compressed and deduplicated backup files. This helps improve recovery time objectives (RTO), minimize disruption and downtime of production workloads. The workloads are recovered in a matter of minutes.

When you perform Instant Recovery, Veeam Backup & Replication mounts workload images to a host directly from backups stored on backup repositories. This means that Veeam Backup & Replication creates fully functioning “temporary spares” with limited I/O performance. To provide full I/O performance, you must migrate these "temporary spares" to the production site. For more information, see [Migration of Recovered VMs to Production Site](#migrate).

Besides disaster recovery matters, Instant Recovery can also be used for testing purposes. Instead of extracting workload images to production storage to perform regular disaster recovery (DR) testing, you can run a workload directly from a backup file, boot it and make sure the guest OS and applications are functioning properly. For more information, see [Finalizing Instant Recovery to VMware vSphere](instant_recovery_review_vm.md).

Instant Recovery supports bulk processing so you can immediately recover multiple workloads at once. If you perform Instant Recovery for several workloads, Veeam Backup & Replication uses the resource scheduling mechanism to allocate and use optimal resources required for Instant Recovery. For details, see [Resource Scheduling](resource_scheduling.md).

Supported Backup Types

You can recover workloads from the following types of backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication

You can also recover VMware vSphere VM data directly from storage snapshots.

* Backups of VMware Cloud Director virtual machines created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows or Veeam Agent for Linux](agents_introduction.md)

* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10)
* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)
* Backups of Google Compute Engine VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)

* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*
* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)
* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2)

\* - Available on Microsoft Windows-based backup server.

How Instant Recovery Works

When Instant Recovery is performed, Veeam Backup & Replication uses the Veeam vPower technology to mount a workload image to an ESXi host directly from a compressed and deduplicated backup file. Since there is no need to extract the workload from the backup file and copy it to production storage, you can perform recovery from any restore point in a matter of minutes.

The image of the workload remains in read-only state to avoid unexpected modifications. By default, all changes to virtual disks that take place while a recovered VM is running are logged to auxiliary redo log files residing on the NFS server (backup server or backup repository). These changes are discarded as soon as the recovered VM is removed, or merged if you migrate the VM to the production site.

To improve I/O performance for a recovered VM, you can redirect VM changes to a specific datastore that is closer to the host where the VM resides. In this case, Veeam Backup & Replication will trigger a snapshot and will put it to the Veeam IR directory on the selected datastore, together with metadata files holding changes to the VM image.

Migration of Recovered VMs to Production Site

To migrate the recovered VMs to the production storage, you can use one of the following relocation methods:

* Use Storage vMotion to quickly migrate the recovered VM to the production storage without any downtime. In this case, original VM data will be pulled from the NFS datastore to the production storage and consolidated with VM changes while the VM is still running. Storage vMotion, however, can only be used if you select to keep VM changes on the NFS datastore without redirecting them. Note that to use Storage vMotion, you need an appropriate VMware license.
* Use Quick Migration. In this case, Veeam Backup & Replication will perform a two-stage migration procedure — instead of pulling data from the vPower NFS datastore, it will recover the VM from the backup file on the production server, then move all changes and consolidate them with the VM data.

For more information on the relocation methods, see [Quick Migration](quick_migration_hv.md). For more information on how to launch the migration for workloads recovered with Instant Recovery, see [Finalizing Instant Recovery to VMware vSphere](instant_recovery_review_vm.md).

Related Topics

[List of Recovery Methods for All Platforms](vm_recovery_all.md)

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
