---
title: "Starting and Stopping Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/jobs_start_stop_web.html"
last_updated: "9/23/2025"
product_version: "13.0.1.1071"
---

# Starting and Stopping Jobs


You can start a job manually if, for example, you want to create an additional restore point for a VM backup or replica without changing the job schedule. You can also stop a job if, for example, VM processing is about to take a long time, and you do not want the job to produce workload on the production environment during business hours.

Starting Jobs

To start a job:

1. In the management pane, click the Jobs node.
2. In the working area, select a backup job and click Start on the ribbon or right-click the job and select Start.

[![Starting and Stopping Jobs](images/start_backup_job_web.webp)](images/start_backup_job_web.webp)

Stopping Jobs

You can stop a job in one of the following ways:

* Stop the job immediately. In this case, Veeam Backup & Replication will produce a new restore point only for those VMs that have already been processed when you stop the job.
* Stop the job after the current VM. In this case, Veeam Backup & Replication will produce a new restore point only for those VMs that have already been processed and for VMs that are being processed at the moment.

To stop a job:

1. In the management pane, click the Jobs node.
2. In the working area, select a backup job and click Stop on the ribbon or right-click the job and select Stop. In the displayed window, click Immediately.

To stop the job after the current VM:

1. In the management pane, click the Jobs node.
2. In the working area, right-click a job and select Stop. In the displayed window, click Gracefully.

[![Starting and Stopping Jobs](images/stop_job_vm_web.webp)](images/stop_job_vm_web.webp)

Related Topics

* [Manual Start of Backup Jobs](scheduling_manual.md)
* [Manual Stop of Backup Jobs](job_sessions_termination.md)


