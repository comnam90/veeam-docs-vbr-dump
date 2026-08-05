---
title: "Retrying Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_retrying_jobs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retrying Jobs


If a job fails, you can retry the backup operation. When you perform a retry, Veeam Backup & Replication restarts the operation only for the failed resources added to the job and does not process VMs that have been processed successfully. As a result, retrying a job takes less time compared to restarting the job for all resources.

To retry a job, do the following:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, right-click the necessary job and select Retry.

Alternatively, select the job and click Retry on the ribbon.

[![Retrying Jobs](images/uh_backup_job_retry.webp)](images/uh_backup_job_retry.webp "Retrying Jobs")

Page updated 2026-01-21

