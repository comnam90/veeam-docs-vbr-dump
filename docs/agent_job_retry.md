---
title: "Retrying Veeam Agent Backup Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_retry.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retrying Veeam Agent Backup Job


You can manually retry a Veeam Agent backup job configured in Veeam Backup & Replication if the job failed during the previous job session. When you retry a Veeam Agent backup job, Veeam Backup & Replication processes only those computers in the job that were not processed successfully during the previous job session.

You can retry a Veeam Agent backup job in one of the following ways:

* [Using Veeam Backup & Replication Console](#console)
* [Using Veeam Backup & Replication Web UI](#webui)

Retrying Veeam Agent Backup Job Using Veeam Backup & Replication Console

To retry a job:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the Veeam Agent backup job and click Retry on the ribbon or right-click the job and select Retry.

|  |
| --- |
| TIP |
| You can also retry a backup job for an individual computer added to this job. To learn more, see [Retrying Job for Individual Computer](#individ). |

[![Retry Backup Job](images/agent_backup_job_retry.webp)](images/agent_backup_job_retry.webp "Retry Backup Job")

Retrying Job for Individual Computer

To retry a backup job for an individual computer:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the Veeam Agent backup job.
4. In the bottom part of Veeam Backup & Replication, find the list of computers that are processed by the selected backup job. In the list, right-click the computer with the Failed status and click Retry.

Keep in mind that you will be able to launch retry for another computer in the same job only after retry finishes for the selected computer.

[![Retry Backup Job for Individual Computer](images/agent_backup_job_retry_one.webp)](images/agent_backup_job_retry_one.webp "Retry Backup Job for Individual Computer")

Retrying Veeam Agent Backup Job Using Veeam Backup & Replication Web UI

To retry a Veeam Agent backup job:

1. In the management pane, click Jobs.
2. Select the check box next to the necessary backup job and click Retry on the toolbar. Alternatively, right-click the job and select Retry.

[![Retry Backup Job](images/agent_job_retry_web.webp)](images/agent_job_retry_web.webp "Retry Backup Job")

Page updated 2026-07-28

