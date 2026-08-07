---
title: "Step 5. Define Job Schedule"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_backup_job_schedule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Define Job Schedule


At the Schedule step of the wizard, you can instruct Veeam Backup & Replication to start the backup job automatically according to a specific backup schedule. The backup schedule defines how often data of the VMs added to the backup job will be backed up.

To help you implement a comprehensive backup strategy, Veeam Backup & Replication allows you to create schedules of the following types:

* Daily — the backup job will run at a specific time on specific days.

To create a daily schedule for the backup job, select the Daily at this time option and define the exact hour when the job will create restore points. Then, use the drop-down list to choose whether you want the backup job to run every day, on weekdays (Monday through Friday) or on specific days.

* Monthly — the backup job will run at a specific time on specific days of specific months.

To create a monthly schedule for the backup job, select the Monthly at this time option and define the exact hour when the job will create restore points. Then, use the drop-down lists to schedule the specific days and months for the backup job to run.

* Periodically — the backup job will run repeatedly throughout a day with a specific time interval.

To create a periodical schedule for the backup job, select the Periodically every option and define the frequency (in hours or minutes) with which the job will create restore points.

|  |
| --- |
| Tip |
| You can instruct Veeam Backup & Replication to run the backup job again if it fails on the first try. To do that, select the Retry failed items processing check box, and specify the maximum number of attempts to run the backup job and the time interval between retries. When retrying backup jobs, Veeam Backup & Replication processes only those VMs that failed to be backed up during the previous attempt. |

![Step 5. Define Job Schedule](images/ovirt_backup_job_add_schedule.webp "Select Restore Point")

Page updated 2026-06-18

