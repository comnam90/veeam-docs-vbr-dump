---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_before_mac.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create a Veeam Agent backup policy in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers and workstations that you plan to add to the Veeam Agent backup policy. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.
* Protection groups that you want to add to the job must be of the computers with pre-installed backup agents type. To learn more, see [Protection Group Types](agents_protection_groups_types.md).

* [For backup jobs targeted at the cloud repository] The Veeam Cloud Connect service provider must be added in the Veeam backup console.

Consider the following about Veeam Agent backup policies:

* After you start managing a Veeam Agent computer with Veeam Backup & Replication, data backup for this computer is performed by a backup job configured in Veeam Backup & Replication. Veeam Agent running on the computer starts a new backup chain on a target location specified in the backup policy settings. You cannot continue the existing backup chain that was created by Veeam Agent operating in the standalone mode.

* You cannot map a Veeam Agent backup policy configured in Veeam Backup & Replication to a Veeam Agent backup chain created by a standalone Veeam Agent on a backup repository.

* Veeam Backup & Replication does not immediately apply backup policy to computers included in protection groups for pre-installed Veeam Agents. Veeam Agents installed on computers that are included in these groups connect to Veeam Backup & Replication every 6 hours and get updated backup policy settings. If you targeted a backup policy at the Veeam backup server and scheduled it earlier than the next connection to Veeam Backup & Replication, this backup policy will be updated on the Veeam Agent computer at the next start of the backup session. To learn more about protection groups for pre-installed Veeam Agents, see [Protection Group Types](agents_protection_groups_types.md).

Keep in mind, that you can immediately update settings of the backup policy from the Veeam Agent computer. To learn more, see [Deploying Veeam Agent for Mac](deploy_agent_mac.md).

* Veeam Agent backup policy may fail unexpectedly due to restrictions applied on the Veeam Agent computer side. For more information, see [Backup Job Restrictions](https://helpcenter.veeam.com/docs/agentformac/userguide/backup_job_restrictions.html) in the Veeam Agent for Mac User Guide.


