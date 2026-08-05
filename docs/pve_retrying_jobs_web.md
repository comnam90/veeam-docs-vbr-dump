---
title: "Retrying Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_retrying_jobs_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retrying Jobs


If a job fails, you can retry the backup operation. When you perform a retry, Veeam Backup & Replication restarts the operation only for the failed resources added to the job and does not process VMs that have been processed successfully. As a result, retrying a job takes less time compared to restarting the job for all resources.

To retry a job, do the following:

1. Navigate to Jobs.
2. Select the failed job.
3. Click Retry.

[![Retrying Job](images/pve_job_retry_web.webp)](images/pve_job_retry_web.webp "Retrying Job")

Page updated 2026-07-27

