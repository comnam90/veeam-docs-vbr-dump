---
title: "Getting Started"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_quickstart.html"
last_updated: "8/5/2025"
product_version: "13.0.1.1071"
---

# Getting Started

In this article

To start using the Veeam Agent management functionality in Veeam Backup & Replication, you must perform the following operations:

1. Deploy Veeam Backup & Replication.

To learn more, see [Deployment](deployment.md).

1. Configure security settings.

By default, Veeam Backup & Replication offers the following settings to establish a secure connection between the backup server and protected computers:

* To establish a secure connection between parties, Veeam Backup & Replication uses the default self-signed certificate.
* Veeam Backup & Replication allows all new Linux hosts to establish a connection to the backup server.

You can use the default security settings or change them if needed. To learn more, see [Configuring Security Settings](agents_manage_tls_and_ssh.md).

1. Add computers that you want to protect with Veeam Agents to the Veeam Backup & Replication inventory.

In Veeam Backup & Replication, computers that you want to protect with Veeam Agents are organized into protection groups. You can use the Veeam Backup & Replication console to create one or more protection groups. To learn more, see [Creating Protection Groups](protection_group_add.md).

1. Discover protected computers and deploy Veeam Agents.

Veeam Backup & Replication is set up to automatically discover protected computers and install Veeam Agent on a discovered computer. By default, these operations are performed immediately after you create a protection group. You can change Veeam Agent discovery and deployment options in the protection group settings, if needed. You can also run discovery and deployment operations manually for an entire protection group, individual Active Directory object in a protection group or individual computer in a protection group. To learn more, see [Working with Protection Groups](protection_group_tasks.md) and [Managing Protected Computers](agents_protected_computers_manage.md).

Make sure to install all available updates for the operating system on the computer you want to protect. Otherwise, the correct functioning of Veeam Agent is not guaranteed.

1. Configure Veeam Agent backup job settings.

You can configure one or more Veeam Agent backup jobs and add to these jobs one or more protection groups, Active Directory objects and individual computers. In Veeam Backup & Replication, you can configure the following types of Veeam Agent backup jobs:

* Veeam Agent backup job managed by the Veeam backup server. To learn more, see [Creating Veeam Agent Backup Jobs](agent_job_create.md).
* Veeam Agent backup job managed by Veeam Agent, or Veeam Agent backup policy. To learn more, see [Creating Veeam Agent Backup Policies](agent_policy.md),

1. Manage Veeam Agent backup jobs and policies.

You can start, stop, enable and disable Veeam Agent backup jobs and policies to administer data protection operations on protected computers. To learn more, see [Managing Veeam Agent Backup Jobs](agent_job_manage_job.md) and [Managing Veeam Agent Backup Policies](agent_job_manage_policy.md).

1. In case of a disaster, you can restore data from a Veeam Agent backup.

To learn more, see [Restoring Data from Veeam Agent Backups](performing_restore_tasks.md).

Page updated 8/5/2025

Page content applies to build 13.0.1.1071
