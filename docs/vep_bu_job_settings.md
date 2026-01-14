---
title: "Required Job Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_bu_job_settings.html"
last_updated: "12/1/2025"
product_version: "13.0.1.1071"
---

# Required Job Settings

In this article

When you create backup jobs, replication jobs, and CDP policies, make sure to enable application-aware processing in the Veeam Backup & Replication console.

You can configure this setting at the Specify Guest Processing Settings step of the job or policy wizard for the relevant hypervisor, cloud or physical platform. For example, see [Specify Guest Processing Settings](backup_job_vss_vm.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication console.

For more information about configuring write-ahead log (WAL) file backup, see the PostgreSQL WAL Files Settings step of the job or policy wizard for the relevant hypervisor, cloud or physical platform. For example, see [PostgreSQL WAL Files Settings](backup_job_vss_postgresql_vm.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication console.

If you do not enable application-aware processing, the created restore points will be crash-consistent only. Browsing data and application item restore from crash-consistent restore points with Veeam Explorer for PostgreSQL is not supported.

Consider the following:

* For backups made with [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/data_protection.html) and [Veeam Plug-in for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/data_protection.html), application-aware processing is not supported.
* For VeeamZIP backups, application-aware processing is not supported. For more information, see [VeeamZIP](veeamzip.md).
* For storage snapshots, application-aware processing is automatically enabled. For more information, see [Application Item Restore from Storage Snapshots](restore_veeam_explorers_snapshots.md).

Page updated 12/1/2025

Page content applies to build 13.0.1.1071
