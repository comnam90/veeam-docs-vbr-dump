---
title: "Working with Veeam Agent Backup Jobs and Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_tasks.html"
last_updated: "6/20/2024"
product_version: "13.0.1.1071"
---

# Working with Veeam Agent Backup Jobs and Policies


To back up data of your protected computers, you must configure a Veeam Agent backup job in Veeam Backup & Replication. The Veeam Agent backup job defines what data to back up, how, where and when to back up data. One Veeam Agent backup job can be used to process one or more protected computers.

In Veeam Backup & Replication, you can create Veeam Agent backup jobs of the following types:

* The backup job that runs on the backup server in the similar way as a regular job for VM data backup. The backup job is intended for protected computers that have permanent connection to the backup server. To learn more, see [Backup Job](agents_job.md).
* The backup policy that describes configuration of individual Veeam Agent backup jobs that run on protected computers. Veeam Backup & Replication uses the backup policy as a saved template and applies settings from the backup policy to Veeam Agents that run on computers added to the backup policy. The backup policy is intended for protected computers that may have limited connection to the backup server. To learn more, see [Backup Policy](agents_policy.md).

After you configured a Veeam Agent backup job in Veeam Backup & Replication, you can manage it in Veeam Backup & Replication as well. Operations available for a Veeam Agent backup job depend on the job mode specified in the job properties:

* For a Veeam Agent backup job managed by the backup server, Veeam Backup & Replication allows you to perform a set of operations similar to a regular backup job for VM data backup. To learn more, see [Managing Veeam Agent Backup Jobs](agent_job_manage_job.md).
* For a Veeam Agent backup job managed by Veeam Agent, or backup policy, Veeam Backup & Replication allows you to perform a set of operations similar to a regular Veeam Agent backup job configured on a Veeam Agent computer. To learn more, see [Managing Veeam Agent Backup Policies](agent_job_manage_policy.md).

One protected computer may be processed with one or more Veeam Agent backup jobs. To learn more, see [Processing One Computer with Multiple Jobs and Policies](agents_job_mode.md#multiple).

|  |
| --- |
| TIP |
| When Veeam Agent operates under control of Veeam Backup & Replication, all data protection, data restore and administration tasks can be performed from the Veeam Backup & Replication console. But some operations are also available on the Veeam Agent computer side. To learn more, see [Operations Available on Veeam Agent Computer](va_operations.md). |

Related Topics

[Veeam Agent Backup Jobs and Policies](agents_job_mode.md)

Related Tasks

* [Creating Agent Backup Job for Windows Computers](agent_job_create_win.md)
* [Creating Agent Backup Policy for Windows Computers](agent_policy_create_win.md)
* [Creating Agent Backup Job for Linux Computers](agent_job_create_linux.md)
* [Creating Agent Backup Policy for Linux Computers](agent_policy_create_linux.md)
* [Creating Agent Backup Policy for Unix Computers](agent_policy_create_unix.md)
* [Creating Agent Backup Policy for Mac Computers](agent_policy_create_mac.md)


