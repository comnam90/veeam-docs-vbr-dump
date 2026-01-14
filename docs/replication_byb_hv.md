---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replication_byb_hv.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a replication job, check the following prerequisites:

* Check requirements and limitations in the [Requirements and Limitations](replica_limitations_hv.md) and [VMs](platform_support.md#vms) sections.

* The version of the target host must be equal to or later than the version of the source host.

* Backup infrastructure components that will take part in the replication process must be added to the backup infrastructure and properly configured. These include source and target Microsoft Hyper-V hosts and backup repository for storing replica metadata. If you want to perform backup in the off-host backup mode, the off-host backup proxy must also be added and properly configured.

The backup server must be able to resolve short names and connect to source and target virtualization hosts.

* The target volume must have enough free space to store disks of replicated VMs. To receive alerts about low space on the target volume, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).
* If you plan to replicate VMs using WAN accelerators, source and target WAN accelerators must be added to the backup infrastructure and properly configured. For more information, see [Adding WAN Accelerators](wan_add.md).
* If you plan to replicate VMs using WAN accelerators, it is recommended that you pre-populate the global cache on the target WAN accelerator before you start the replication job. Global cache population helps reduce the amount of traffic transferred over WAN. For more information, see [Populating Global Cache](wan_populate_cache.md).
* If you plan to replicate VMs from the backup, the backup job that you plan to use as the source must be configured beforehand. For more information, see [Replica from Backup](replica_from_backup_hv.md).
* If you plan to use pre-job, post-job, pre-freeze or post-thaw scripts, you must create scripts before you configure the replication job. For the supported script format, see [Pre-Freeze and Post-Thaw Scripts](pre_post_scripts_hv.md).

* [For Linux-based backup server] The following applies to pre-job and post-job scripts:

* Bash scripts must use Linux-style line ednings (LF).
* Only the .SH and .PS1 file extensions are supported.

* Scripts with the .EXE file extension are not supported.
* Script impersonation is not supported.

To upload scripts to the Linux backup server, in the Veeam Backup & Replication console, navigate to the Files node. Then, copy script files to the /var/lib/veeam/scripts folder on the Linux backup server.

Page updated 10/21/2025

Page content applies to build 13.0.1.1071
