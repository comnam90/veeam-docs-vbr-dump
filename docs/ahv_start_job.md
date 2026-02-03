---
title: "Starting and Stopping Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_start_job.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Starting and Stopping Jobs


You can start a backup job manually, for example, if you want to create an additional restore point and do not want to modify the configured job schedule. You can also stop a backup job manually if processing of a VM is about to take too long, and you do not want the job to have an impact on the production environment during business hours. When you stop a running job, Veeam Backup & Replication creates a new restore point only for those VMs that have already been processed by the time you stop the job.

To start or stop a backup job, do the following:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, right-click the necessary job and select Start or Stop.

Alternatively, select the job and click Start or Stop on the ribbon.

[![Starting and Stopping Jobs](images/ahv_job_start.webp)](images/ahv_job_start.webp "Starting and Stopping Jobs")


