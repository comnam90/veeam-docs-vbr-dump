---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_before_linux.html"
last_updated: "11/27/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a Veeam Agent backup job managed by the backup server in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers and workstations that you plan to add to the Veeam Agent backup job. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the job must be configured in advance.

Veeam Agent backup jobs have the following limitations:

* If you want to perform a volume-level restore of a machine using Veeam Agent, the BIOS boot partition of this machine must be associated with a block device. Otherwise, Veeam Agent supports only file-level restore from the backup of the machine.
* You can create Veeam Agent backups in a Veeam backup repository and Veeam Cloud Connect repository. If you want to save backups in other target locations, you must configure a Veeam Agent backup job managed by Veeam Agent (backup policy). To learn more, see [Creating Policy for Linux Computers](agent_policy_create_linux.md).

* You cannot map a Veeam Agent backup job managed by the backup server to a Veeam Agent backup chain created by another type of a Veeam Agent backup job. After you change the mode of a Veeam Agent computer, Veeam Backup & Replication starts a new backup chain in a target location specified in the backup job settings.

* Veeam Agent does not support creating transaction log backups in the cloud repository. You cannot enable transaction log backup options in the properties of the backup job targeted at the cloud repository.
* Veeam Agent does not support backup of bind mount points. In the scope of the backup job, you must specify the path to the original mount point instead.

If you perform an entire machine backup of a system with bind mount points, Veeam Agent will back up only the data from the original mount points. Veeam Agent will not back up the bind mount points themselves and will not replicate the bind mount configuration in the backup. After restore, you may need to manually reconfigure any bind mounts that existed on the original system.

* If you plan to create a Veeam Agent backup job for computers with nosnap Veeam Agent installed, consider the limitations and system requirements listed in section [System Requirements for Linux Computers (nosnap Veeam Agent)](agents_system_requirements_linux_nosnap.md).

* You cannot add a Veeam Agent computer protected by a Veeam Agent backup policy to a backup job managed by the backup server. To add such a computer to a backup job managed by the backup server, first remove the computer from the Veeam Agent backup policy.

Page updated 11/27/2025

Page content applies to build 13.0.1.1071
