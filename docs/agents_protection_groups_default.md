---
title: "Predefined Protection Groups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protection_groups_default.html"
last_updated: "12/8/2025"
product_version: "13.0.1.1071"
---

# Predefined Protection Groups

In this article

In addition to protection groups created by a user, the Veeam Backup & Replication inventory may contain one or more predefined protection groups.

Manually Added

The Manually Added protection group contains individual computers added to Veeam Agent backup jobs configured in Veeam Backup & Replication. This protection group is aimed for scenarios when you want to manage a single Veeam Agent computer or a small number of Veeam Agent computers and do not want to create additional protection groups. Veeam Backup & Replication automatically adds a computer to the Manually Added protection group when you add this computer to a Veeam Agent backup job. To learn more, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).

|  |
| --- |
| NOTE |
| The Manually Added protection group cannot contain computers with Veeam Agent for Mac or Veeam Agent for Linux on Power. To work with such computers, use [protection groups for pre-installed Veeam Agents](agents_protection_groups_types.md#flexible). |

The Manually Added protection group has the following limitations:

* For the Manually Added protection group, you can change only a limited number of settings:

* You can change discovery and deployment options. (Except for changing the distribution server. For the Manually Added protection group, the role of the distribution server is always assigned to the backup server.)
* You can remove computers from this protection group. For example, you may want to remove a computer from a Manually Added protection group if you do not want to back up data of this computer any longer, and you have removed this computer from a Veeam Agent backup job.
* You cannot change other settings, such as the name and type of this protection group.

* You cannot add the entire Manually Added protection group to a Veeam Agent backup job.

Unmanaged

The Unmanaged protection group acts as a filter to display unmanaged Veeam Agent computers, that is, computers that meet the following conditions:

1. Have Veeam Agent deployed and configured directly from a Veeam Agent computer or with Veeam Service Provider Console.
2. Run a Veeam Agent backup job targeted at a backup repository managed by Veeam Backup & Replication.

You cannot perform any operations with the Unmanaged protection group, as well as add computers included in this group to a Veeam Agent backup job. However, you can move such computers to a protection group that you created. To learn more, see [Moving Unmanaged Computer to Protection Group](agents_protected_computers_move.md).

After you move an unmanaged computer to a protection group, Veeam Backup & Replication will start managing Veeam Agent running on this computer according to discovery settings specified in the properties of the protection group. If the protection group is added to a Veeam Agent backup job, Veeam Backup & Replication will add the new computer to the job, too. You will no longer be able to manage Veeam Agent directly on the Veeam Agent computer or from Veeam Service Provider Console.

Out of Date

The Out of Date protection group is displayed when Veeam Backup & Replication discovers protected computers on which an outdated version of Veeam Agent is installed. For example, this may happen in a situation where you configure a protection group with Veeam Agent deployment options disabled, and Veeam Backup & Replication detects a newer version of Veeam Agent during discovery.

|  |
| --- |
| NOTE |
| Only computers with supported for upgrade Veeam Agents are displayed in this group. To learn more, see [Upgrading Veeam Agent](agents_protected_computers_upgrade.md). |

The Out of Date protection group lets you update Veeam Agent on multiple computers at once. To learn more, see [Upgrading Veeam Agent on Multiple Computers](agents_protected_computers_upgrade.md#upgrade).

Offline

The Offline protection group acts as a filter to display computers to which Veeam Backup & Replication could not connect during the latest rescan session.

Untrusted

The Untrusted protection group displays Linux-based and Microsoft Windows-based computers whose fingerprints have not been verified in Veeam Backup & Replication. To learn more, see [Validating Untrusted Hosts](linux_fingerprint_validate.md).

Page updated 12/8/2025

Page content applies to build 13.0.1.1071
