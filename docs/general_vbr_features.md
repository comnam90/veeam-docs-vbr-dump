---
title: "Platform-Independent Features"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/general_vbr_features.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Platform-Independent Features

In this article

Veeam Backup & Replication is a data protection solution designed to support a [wide range of platforms](platform_support.md), including virtual, physical, cloud platforms and others. While many features are designed as platform-specific, Veeam Backup & Replication also offers a set of platform-independent features. These features enhance the overall functionality, usability and efficiency of the solution.

This section describes the following platform-independent features:

* [Backup copy](backup_copy.md). The backup copy feature creates additional backup copies from existing backups, enabling offsite storage for disaster recovery purposes.
* [Data recovery (All Platforms)](data_recovery_all.md). Robust data recovery capabilities allow you to quickly and efficiently recover entire VMs, disks, or application items. Veeam Backup & Replication also provides recovery across different platforms. For example, you can recover your workloads to VMware vSphere, Hyper-V, Microsoft Azure and other platforms.
* [File copy](file_copy.md). The file copy feature allows you to create copies of specific files or folders from backup repositories to different locations. This functionality is useful for organizing data, ensuring compliance, or preparing files for sharing or transfer.
* [VeeamZIP](veeamzip.md). VeeamZIP is a lightweight backup solution that enables you to create a full backup of your workload as a single file. This feature allows quick and easy backup creation without the need for a predefined job.
* [Tape device integration and management](tape_device_support.md). The integration with tape devices allows you to store backups on tape as part of a long-term retention strategy. This feature includes management capabilities for creating, monitoring, and restoring backups from tape, ensuring data is archived securely and efficiently.
* [Storage system snapshot integration](storage_integration.md). This integration allows the use of storage system snapshots to create backups and snapshot chains. By integrating with storage systems, Veeam Backup & Replication accelerates the backup process and minimizes the impact on the production site.

For the information on platform-specific features, see [Platform-Specific Features](workloads.md).

Page updated 12/3/2025

Page content applies to build 13.0.1.1071
