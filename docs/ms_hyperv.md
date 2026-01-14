---
title: "Microsoft Hyper-V"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ms_hyperv.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# Microsoft Hyper-V

In this article

Veeam Backup & Replication offers various data protection and disaster recovery features for the Microsoft Hyper-V environment.

* Backup. Veeam Backup & Replication creates image-level backups of VMs, ensuring data integrity and consistency. One of the backup features is application-aware processing, which quiesces applications during the backup process to capture a consistent state, particularly for databases like Microsoft SQL Server, Exchange and others. This enables organizations to restore applications and their data accurately and efficiently. For more information, see [Backup (Microsoft Hyper-V)](backup_hv.md).
* Replication. Veeam Backup & Replication creates replicas in a secondary location, ensuring data redundancy and minimizing downtime in the event of a site failure. Replication is helpful for scenarios where organizations need to maintain a copy of virtual machines at specific intervals, commonly hours. This approach balances data loss and performance impact, making it an effective solution for disaster recovery. This is a manageable solution for environments that do not require the instantaneous recovery capabilities. For more information, see [Replication (Microsoft Hyper-V)](replication_hv.md).
* Data recovery. Veeam Backup & Replication offers rapid and flexible recovery options including entire VM recovery with stages restore and VM file recovery. For more information, see [Data Recovery (Microsoft Hyper-V)](data_recovery_hv.md). In addition to the recovery methods specific for Hyper-V, you can also use platform-independent recovery. Platform-independent recovery includes recovery to other platforms, such as VMware vSphere, Microsoft Azure, AWS and Google Cloud. For more information, see [Data Recovery (All Platforms)](data_recovery_all.md).
* Recovery verification. Recovery verification ensures that backups and replicas are recoverable and functional. Veeam Backup & Replication automatically tests backups and replicas in an isolated environment. SureBackup powers on backed-up virtual machines in a secure setting, running predefined tests to verify their integrity and operational status. For more information, see [Recovery Verification (Microsoft Hyper-V)](recovery_verification_overview_hv.md).
* On-Demand Sandbox. On-Demand Sandbox allows you to create isolated environments for testing and development purposes, and use production data without affecting live workloads. This feature enables safe testing of applications, updates and changes. It facilitates better change management and quality assurance without the risks associated with working directly in the production environment. For more information, see [On-Demand Sandbox](sandbox_hv.md).
* Built-in reporting. Veeam Backup & Replication provides comprehensive reporting on backup and replication activities. You can access reports that show the status of backup jobs, replication jobs, and overall backup infrastructure health. This allows you to quickly identify any issues or bottlenecks. For more information, see [Reporting](reporting_hv.md). For more in-depth reporting, you can use Veeam reporting solutions. For more information, see [Extended Management and Reporting](management.md).

In addition to the listed features specific to Microsoft Hyper-V, Veeam Backup & Replication provides features that are available for all platforms, such as backup copy, recovery to different platforms and others. For more information, see [Platform-Independent Features](general_vbr_features.md).

In This Section

* [System Requirements (Microsoft Hyper-V)](system_requirements_hv.md)
* [Backup (Microsoft Hyper-V)](backup_hv.md)
* [Replication (Microsoft Hyper-V)](replication_hv.md)
* [Data Recovery (Microsoft Hyper-V)](data_recovery_hv.md)
* [Recovery Verification (Microsoft Hyper-V)](recovery_verification_overview_hv.md)
* [On-Demand Sandbox](sandbox_hv.md)

Page updated 12/30/2025

Page content applies to build 13.0.1.1071
