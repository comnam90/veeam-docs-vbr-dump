---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_flr_considerations_common.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

This section lists considerations and limitations common for recovery guest OS files and folders from Microsoft Windows and Linux workloads. For information on considerations and limitations specific for recovering Microsoft Windows and Linux workloads, see [Microsoft Windows Limitations and Considerations Guest OS Recovery](guest_restore_before_you_begin.md) and [Linux Limitations and Considerations Guest OS Recovery](multios_restore_before_you_begin.md).

Infrastructure Components

* You can recover files from the file systems listed in section [Supported Platforms, Applications and Workloads](platform_support.md#flr).
* If you plan to use a mount server (default or associated with a repository) as a mount server for guest OS restore, see [Mount Server Requirements](system_requirements.md#mount).

Source for Data Recovery

* [For Hyper-V VMs] See limitations in the [VMs](platform_support.md#vms) section of [Supported Platforms, Applications and Workloads](platform_support.md).

* You can recover guest OS files from a backup, replica, Cloud Director replica or CDP replica that has at least one successfully created restore point.

* You cannot recover files from a backup created in the reverse incremental mode if the backup job is running. If the backup is created in the incremental backup mode and the backup job is being performed, you can recover files from any available restore point.

* [For vSphere] You cannot recover guest OS files from a running VM replica or if the replication job with the necessary VM is being performed. However, recovery is possible for CDP replicas if the CDP policy is running.

Target for Data Recovery

* [Using Veeam Backup & Replication web UI](performing_guest_restore_web.md) for guest OS file recovery to another location is not supported. [Use the Veeam Backup & Replication console](performing_guest_restore.md) instead.

* If you plan to recover guest OS files to their original location or to another VM of the same platform, check the following:

* [For vSphere] VMware Tools or OpenVM Tools are installed and running on the target workload.
* [For Hyper-V] Hyper-V Integration Services are installed and on the target workload.

Linux Helper Host as Mount Server

If you plan to use a Linux helper host as a mount server (select the <Linux\_host\_name> or Specify a different Linux host option at the [Restore point](multios_restore_host_vm.md) step), consider the following:

* Check the supported OSes listed in [System Requirements](system_requirements.md#helper_host).
* The backup server and the mount server, associated with the repository where the backup is stored, must be able to resolve the FQDN of the helper host.
* You can recover from ZFS if the zfsutils-linux package is installed on the specified Linux helper host. The zfs-fuse package is not supported.
* The Linux helper host OS kernel must support the file system that you plan to mount on this host. Otherwise, mount will be refused, and, in rare cases, it may cause kernel panic.
* Make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get an error with the permission denial.
* For the Linux helper host option, mounting of LVM snapshots is not supported. Thus, LVM snapshots are skipped from processing.

* Recovery from a Btrfs disk using the original server as the Linux helper host is not possible. The issue occurs due to the restriction of mounting two Btrfs disks with identical IDs to the same machine. To avoid this issue, use the helper appliance option or a different Linux-based server that supports Btrfs. However, note that Btrfs disks can be recovered for backups created by Veeam Agent for Linux. During the backup process, Veeam Agent for Linux changes disk IDs in the backup file.
* Recovery from a ZFS pool using the original server as the mount server is not possible. The issue occurs due to the restriction of mounting two ZFS pools with identical UUIDs to the same machine. To avoid this issue, use the helper appliance option or a different Linux-based server that supports ZFS pools.
* [Hardened repositories](hardened_repository.md) cannot be selected as Linux helper hosts.

CDP Replicas

* You can launch restore for a CDP replica if its CDP policy is currently running. CDP will continue working.
* During restore, the CDP policy does not create new long-term restore points and does not delete the existing ones. Short-term restore points are still created.
* You cannot launch guest OS file restore, SureReplica, application item restore and failover in parallel for one VM or replica.

Storage Snapshots

Requirements for guest OS file restore from storage snapshots are listed in the [Data Recovery from Storage Snapshots](storage_limitations_general.md#vess) section.

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
