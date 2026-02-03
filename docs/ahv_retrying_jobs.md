---
title: "Retrying Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_retrying_jobs.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Retrying Jobs


If a job fails, you can retry the backup operation. When you perform a retry, Veeam Backup & Replication restarts the operation only for the failed resources added to the job and does not process VMs that have been processed successfully. As a result, retrying a job takes less time compared to restarting the job for all resources.

To retry a job, do the following:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, right-click the necessary job and select Retry.

Alternatively, select the job and click Retry on the ribbon.

[![Retrying Job](images/ahv_job_retry.webp)](images/ahv_job_retry.webp "Retrying Job")


