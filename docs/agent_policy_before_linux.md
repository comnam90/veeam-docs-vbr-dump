---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_before_linux.html"
last_updated: "11/27/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create a Veeam Agent backup policy in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers and workstations that you plan to add to the backup policy. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.

* [For backup policies targeted at a cloud repository] The Veeam Cloud Connect service provider must be added in the Veeam backup console.

Veeam Agent backup policies have the following limitations:

* If you want to perform a volume-level restore of a computer using Veeam Agent, the BIOS boot partition of this computer must be associated with a block device. Otherwise, Veeam Agent supports only file-level restore from the backup of the computer.

* You cannot map a Veeam Agent backup policy to a Veeam Agent backup chain created by another type of a Veeam Agent backup job. After you change the mode of a Veeam Agent computer, Veeam Backup & Replication starts a new backup chain in a target location specified in the backup policy settings.

* Veeam Agent does not support creating transaction log backups in the cloud repository. You cannot enable transaction log backup options in the properties of the backup policy targeted at the cloud repository.
* Veeam Agent does not support backup of bind mount points. In the scope of the backup job, you must specify the path to the original mount point instead.

If you perform an entire machine backup of a system with bind mount points, Veeam Agent will back up only the data from the original mount points. Veeam Agent will not back up the bind mount points themselves and will not replicate the bind mount configuration in the backup. After restore, you may need to manually reconfigure any bind mounts that existed on the original system.

* [For backup policies that protect computers with nosnap Veeam Agent] Consider the system requirements and limitations listed in section [System Requirements for Linux Computers (nosnap Veeam Agent)](agents_system_requirements_linux_nosnap.md).
* [For backup policies that protect computers with nosnap Veeam Agent] Nosnap versions of Veeam Agent for Linux do not support application-aware processing. If you configure application-aware processing in a policy that protects computers with nosnap Veeam Agent, such policy will fail to get applied or updated on the computers with nosnap Veeam Agent.

* You cannot add a Veeam Agent computer protected by a backup job managed by the backup server to a Veeam Agent backup policy. To add such a computer to a Veeam Agent backup policy, first remove the computer from the backup job managed by the backup server.


