---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_before_unix.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a Veeam Agent backup policy in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers that you plan to add to the Veeam Agent backup policy. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.
* Protection groups that you want to add to the policy must be of the computers with pre-installed backup agents type. You can also add protection groups of the individual computers and computers from CSV file type. To learn more, see [Protection Group Types](agents_protection_groups_types.md).

Veeam Agent backup policies have the following limitations:

* After you start managing a Veeam Agent computer with Veeam Backup & Replication, data backup for this computer is performed by a backup job configured in Veeam Backup & Replication. Veeam Agent running on the computer starts a new backup chain on a target location specified in the backup policy settings. You cannot continue the existing backup chain that was created by Veeam Agent operating in the standalone mode.

* You cannot map a Veeam Agent backup policy configured in Veeam Backup & Replication to a Veeam Agent backup chain created by a standalone Veeam Agent on a backup repository.
* Veeam Backup & Replication does not immediately apply backup policy to computers included in protection groups for pre-installed Veeam Agents. Veeam Agents installed on computers that are included in these groups connect to Veeam Backup & Replication every 6 hours and get updated backup policy settings. If you targeted a backup policy at the Veeam backup server and scheduled it earlier than the next connection to Veeam Backup & Replication, this backup policy will be updated on the Veeam Agent computer at the next start of the backup session. To learn more about protection groups for pre-installed Veeam Agents, see [Protection Group Types](agents_protection_groups_types.md).

Keep in mind, that you can immediately update settings of the backup policy from the Veeam Agent computer. To learn more, see [Deploying Veeam Agent for Unix](deploy_agent_unix.md#configure).

Page updated 7/29/2025

Page content applies to build 13.0.1.1071
