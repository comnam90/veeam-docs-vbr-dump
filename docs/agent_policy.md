---
title: "Creating Veeam Agent Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# Creating Veeam Agent Backup Policies


To create a Veeam Agent backup policy, you must create a backup job with the Managed by agent option selected in the job settings. In contrast to a Veeam Agent backup job managed by the backup server that is similar to a regular backup job for VM backup, a backup policy acts as a template that describes settings of individual Veeam Agent backup jobs running on protected computers.

Veeam Backup & Replication lets you create backup policies for the following types of protected computers:

* [Microsoft Windows computers protected with Veeam Agent for Microsoft Windows](agent_policy_create_win.md)
* [Linux computers protected with Veeam Agent for Linux](agent_policy_create_linux.md)
* [Unix computers protected with Veeam Agent for Unix](agent_policy_create_unix.md)
* [macOS computers protected with Veeam Agent for Mac](agent_policy_create_mac.md)

Consider the following:

* After you create a Veeam Agent backup policy, Veeam Backup & Replication connects to protected computers added to the backup policy and applies settings specified in the policy to configure the Veeam Agent backup job on each computer.
* You must create a Veeam Agent backup policy if you want to protect computers with pre-installed Veeam Agents. To learn more, see [Protection Group Types](agents_protection_groups_types.md).
* Veeam Backup & Replication does not connect to the protected computers added to the protection group for pre-installed Veeam Agents. In case of this protection group, computers connect to the Veeam backup server and become members of the protection group after Veeam Agent deployment. To learn more, see [Protection Group Types](agents_protection_groups_types.md).
* You cannot create a Veeam Agent backup policy if you want to protect cloud machines. In this case, you must create a Veeam Agent backup job managed by the backup server. To learn more, see [Creating Veeam Agent Backup Jobs](agent_job_create.md#cloud)

Related Topics

[Backup Policy](agents_policy.md)


