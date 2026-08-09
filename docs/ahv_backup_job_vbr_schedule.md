---
title: "Step 6. Specify Job Scheduling Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_backup_job_vbr_schedule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Specify Job Scheduling Options


At the Schedule step of the wizard, you can instruct Veeam Backup & Replication to start the backup job automatically according to a specific backup schedule. The backup schedule defines how often data of the VMs added to the backup job will be backed up.

To help you implement a comprehensive backup strategy, Veeam Backup & Replication allows you to create schedules of the following types:

* Daily — the backup job will run at a specific time on specific days.

To create a daily schedule for the backup job, select the Daily at this time option and define the exact hour when the job will create restore points. Then, use the drop-down list to choose whether you want the backup job to run every day, on weekdays (Monday through Friday) or on specific days.

* Monthly — the backup job will run at a specific time on specific days of specific months.

To create a monthly schedule for the backup job, select the Monthly at this time option and define the exact hour when the job will create restore points. Then, use the drop-down lists to schedule the specific days and months for the backup job to run.

* Periodically — the backup job will run repeatedly throughout a day with a specific time interval.

To create a periodical schedule for the backup job, select the Periodically every option and define the frequency (in hours or minutes) with which the job will create restore points.

To prevent backup operations from overlapping with production hours, it is recommended that you configure a time interval during which Veeam Backup & Replication is allowed to create restore points; to do that, click Schedule and configure the necessary interval.

|  |
| --- |
| Tip |
| You can instruct Veeam Backup & Replication to run the backup job again if it fails on the first try. To do that, select the Retry failed items processing check box, and specify the maximum number of attempts to run the backup job and the time interval between retries. When retrying backup jobs, Veeam Backup & Replication processes only those VMs that failed to be backed up during the previous attempt. |

![Step 6. Specify Job Scheduling Options](images/ahv_backup_job_add_vbr_schedule.webp "Define Job Schedule")

Page updated 2026-07-16

