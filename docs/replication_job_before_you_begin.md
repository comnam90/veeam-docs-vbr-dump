---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replication_job_before_you_begin.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a replication job, check the following prerequisites and limitations:

* Check limitations for replication described in section [Considerations and Limitations](replica_limitations.md).

* Backup infrastructure components that will take part in the replication process must be added to the backup infrastructure and properly configured. These include source and target ESXi hosts, one backup proxy for on-site replication scenario or two backup proxies for off-site replication scenario and backup repository for storing replica metadata. For more information, see [Backup Infrastructure for Replication](replication_components.md).
* The backup server must be able to resolve short names and connect to source and target virtualization hosts.

* The target datastore must have enough free space to store disks of replicated VMs. To receive alerts about low space on the target datastore, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).
* If you plan to replicate VMs using WAN accelerators, source and target WAN accelerators must be added to the backup infrastructure and properly configured. For more information, see [Adding WAN Accelerators](wan_add.md).
* If you plan to replicate VMs using WAN accelerators, it is recommended that you pre-populate global cache on the target WAN accelerator before you start the replication job. Global cache population helps reduce the amount of traffic transferred over WAN. For more information, see [Manually Populating Global Cache](wan_populate_cache.md).
* If you plan to replicate VMs from a backup, the backup job that you plan to use as the source must be configured beforehand. For more information, see [Replica from Backup](replica_from_backup.md).
* If you plan to use pre-job and post-job scripts and pre-freeze and post-thaw scripts, you must create scripts before you configure the replication job. For the supported script format, see [Pre-Freeze and Post-Thaw Scripts](pre_post_scripts.md#scripts).

* If you plan to protect VMware Cloud Director objects, consider using the dedicated replication job. For more information, see [Replication for VMware Cloud Director](vcloud_director_replication.md).

* [For Linux-based backup server] The following applies to pre-job and post-job scripts:

* Bash scripts must use Linux-style line ednings (LF).
* Only the .SH and .PS1 file extensions are supported.

* Scripts with the .EXE file extension are not supported.
* Script impersonation is not supported.

To upload scripts to the Linux backup server, in the Veeam Backup & Replication console, navigate to the Files node. Then, copy script files to the /var/lib/veeam/scripts folder on the Linux backup server.

Page updated 10/21/2025

Page content applies to build 13.0.1.1071
