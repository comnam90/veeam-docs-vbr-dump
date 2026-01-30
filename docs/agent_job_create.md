---
title: "Creating Veeam Agent Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_create.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Creating Veeam Agent Backup Jobs


To create a Veeam Agent backup job managed by the backup server, you must create a backup job with the Managed by backup server option selected in the job settings. You will be able to add one or more individual computers and protection groups to the job and instruct Veeam Backup & Replication to create Veeam Agent backups in a Veeam backup repository or Veeam Cloud Connect repository. The Veeam Agent backup job will run on the backup server in the similar way as a regular job for VM data backup. To learn more, see [Backup Job](agents_job.md).

Veeam Backup & Replication lets you create backup jobs for the following types of protected computers:

* [Microsoft Windows computers protected with Veeam Agent for Microsoft Windows](agent_job_create_win.md)
* [Linux computers protected with Veeam Agent for Linux](agent_job_create_linux.md)

If you want to protect a computer running Unix or macOS, you must create a backup job managed by Veeam Agent (backup policy). To learn more, see [Creating Policy for Unix Computers](agent_policy_create_unix.md) and [Creating Policy for Mac Computers](agent_policy_create_mac.md).

Related Topics

[Backup Job](agents_job.md)


