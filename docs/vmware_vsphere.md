---
title: "VMware vSphere"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vmware_vsphere.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# VMware vSphere

In this article

Veeam Backup & Replication offers various data protection and disaster recovery features for the VMware vSphere environment.

* Backup. Veeam Backup & Replication creates image-level backups of VMs, ensuring data integrity and consistency. One of the backup features is application-aware processing, which quiesces applications during the backup process to capture a consistent state, particularly for databases like Microsoft SQL Server, Exchange and others. This enables organizations to restore applications and their data accurately and efficiently. For more information, see [Backup (VMware vSphere)](backup.md).
* Replication. Veeam Backup & Replication creates replicas in a secondary location, ensuring data redundancy and minimizing downtime in the event of a site failure. Replication is helpful for scenarios where organizations need to maintain a copy of virtual machines at specific intervals, commonly hours. This approach balances data loss and performance impact, making it an effective solution for disaster recovery. This is a manageable solution for environments that do not require the instantaneous recovery capabilities. For more information, see [Replication (VMware vSphere)](replication.md).
* Continuous Data Protection (CDP). CDP offers near-instantaneous replication of VM changes, enabling recovery point objectives (RPOs) of seconds. This feature is helpful for mission-critical applications that require minimal data loss and rapid recovery. For more information, see [Continuous Data Protection (CDP) (VMware vSphere)](cdp_replication.md).
* Data recovery. Veeam Backup & Replication offers rapid and flexible recovery options, including entire VM recovery, Instant Disk Recovery, Instant FCD Disk Recovery, VM files recovery and others. For more information, see [Data Recovery (VMware vSphere)](data_recovery.md). In addition to the recovery methods specific for VMware vSphere, you can also use platform-independent recovery. Platform-independent recovery includes recovery to other platforms, such as Microsoft Hyper-V, Microsoft Azure, AWS, and Google Cloud. For more information, see [Data Recovery (All Platforms)](data_recovery_all.md).
* Recovery verification. Recovery verification ensures that backups and replicas are recoverable and functional. Veeam Backup & Replication automatically tests backups and replicas in an isolated environment. SureBackup powers on backed-up virtual machines in a secure setting, running predefined tests to verify their integrity and operational status. SureReplica performs similar validation for replicated VMs, ensuring they are ready for failover. For more information, see [Recovery Verification (VMware vSphere)](recovery_verification_overview.md).
* On-Demand Sandbox. On-Demand Sandbox allows you to create isolated environments for testing and development purposes, and use production data without affecting live workloads. This feature enables safe testing of applications, updates and changes. It facilitates better change management and quality assurance without the risks associated with working directly in the production environment. For more information, see [On-Demand Sandbox](sandbox.md).
* Quick Migration. Quick Migration allows you to migrate VMs or virtual disks between ESXi hosts and datastores. Veeam Backup & Replication supports migration of VMs or their disks in any state with minimum disruption to business operations. You can use Quick Migration as a self-contained capability or as a way to finalize the Instant Recovery and Instant Disk Recovery processes. For more information, see [Quick Migration](quick_migration.md).
* VM Copy. VM copy allows you to create an independent fully functioning copy of a VM or VM container (host, cluster, folder, resource pool, VirtualApp, datastore or tag) on the selected storage. The copy is stored decompressed, in the native VMware vSphere format, so it can be started right away. This feature allows you to duplicate VMs for testing, development or archiving purposes.
* Built-in reporting. Veeam Backup & Replication provides comprehensive reporting on backup and replication activities. You can access reports that show the status of backup jobs, replication jobs, and overall backup infrastructure health. This allows you to quickly identify any issues or bottlenecks. For more information, see [Reporting](reporting.md). For more in-depth reporting, you can use Veeam reporting solutions. For more information, see [Extended Management and Reporting](management.md).
* Advanced VMware features. Veeam Backup & Replication supports advanced VMware capabilities such as VMware vSphere tags for job management, encrypted VMs and storage policies. For more information, see [Advanced VMware vSphere Features](vmware_features.md).
* VMware Cloud Support. Veeam Backup & Replication offers support for VMware Cloud environments, enabling backup, recovery and replication of workloads running in VMware Cloud on AWS and other VMware-based cloud infrastructures. For more information, see [VMware Cloud Support](vmware_cloud_support.md).

In addition to the listed features specific to VMware vSphere, Veeam Backup & Replication provides features that are available for all platforms, such as backup copy, recovery to different platforms and others. For more information, see [Platform-Independent Features](general_vbr_features.md).

In This Section

* [System Requirements (VMware vSphere)](system_requirements_vm.md)
* [Backup (VMware vSphere)](backup.md)
* [Replication (VMware vSphere)](replication.md)
* [Continuous Data Protection (CDP) (VMware vSphere)](cdp_replication.md)
* [Data Recovery (VMware vSphere)](data_recovery.md)
* [Recovery Verification (VMware vSphere)](recovery_verification_overview.md)
* [On-Demand Sandbox](sandbox.md)
* [Quick Migration](quick_migration.md)
* [VM Copy](vm_copy.md)
* [Advanced VMware vSphere Features](vmware_features.md)
* [VMware Cloud Support](vmware_cloud_support.md)

Page updated 12/30/2025

Page content applies to build 13.0.1.1071
