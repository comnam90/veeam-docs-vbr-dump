---
title: "Instant Recovery to Microsoft Azure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_to_azure.html"
last_updated: "12/11/2025"
product_version: "13.0.1.1071"
---

# Instant Recovery to Microsoft Azure


With Instant Recovery to Microsoft Azure, you can immediately recover different workloads (VMs, EC2 instances, physical servers, and so on) as Microsoft Azure VMs. This feature is useful, if you want to recover your infrastructure in a matter of minutes but with limited performance. To migrate your infrastructure, use the [Restore to Microsoft Azure](restore_azure.md) feature.

During recovery, Veeam Backup & Replication runs workloads from compressed and deduplicated backup files. This approach helps improve recovery time objectives (RTO), and minimizes disruption and downtime of production workloads. The workloads are recovered in a matter of minutes.

When you perform Instant Recovery, Veeam Backup & Replication creates dummy VMs and mounts disks of workloads to these VMs directly from backups. The dummy VMs have limited I/O performance. To achive full I/O performance, you must migrate the VMs to the production site.

In addition to disaster recovery, you can also use Instant Recovery for testing purposes. Instead of extracting workloads to production storage for regular disaster recovery (DR) testing, you can run a workload directly from a backup file. This allows you to boot the workload and verify that the guest OS and applications function properly. For more information, see [Finalizing Instant Recovery to Microsoft Azure](ir_azure_finalize.md).

Instant Recovery supports bulk processing, allowing you to recover multiple workloads at once. When you perform Instant Recovery for several workloads, Veeam Backup & Replication uses the resource scheduling mechanism to allocate and use optimal resources required for Instant Recovery. For details, see [Resource Scheduling](resource_scheduling.md).

Supported Backup Types

You can recover workloads from the following types of backups:

* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows or Veeam Agent for Linux](agents_introduction.md)

* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)

* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10)
* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)

* Backups of Google Compute Engine VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*

* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*

* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)

\* - Available on Microsoft Windows-based backup server.


