---
title: "Creating Veeam Agent Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_create.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Veeam Agent Backup Jobs


To create a Veeam Agent backup job managed by the backup server, launch the New Agent Backup Job wizard and choose to have the job managed by the backup server. You will be able to add one or more individual computers and protection groups to the job and instruct Veeam Backup & Replication to create Veeam Agent backups in a Veeam backup repository or Veeam Cloud Connect repository. The Veeam Agent backup job will run on the backup server in the similar way as a regular job for VM data backup. To learn more, see [Backup Job](agents_job.md).

Veeam Backup & Replication lets you create backup jobs for the following types of protected computers:

* [Microsoft Windows computers protected with Veeam Agent for Microsoft Windows](agent_job_create_win.md)
* [Linux computers protected with Veeam Agent for Linux](agent_job_create_linux.md)
* [Unix computers protected with Veeam Agent for Unix](agent_job_unix_create.md)

If you want to protect a computer running macOS, you must create a backup job managed by Veeam Agent (backup policy). To learn more, see [Creating Policy for Mac Computers](agent_policy_create_mac.md).

Related Topics

[Backup Job](agents_job.md)

Page updated 2026-07-16

