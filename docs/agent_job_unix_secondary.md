---
title: "Step 9. Specify Secondary Target"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_unix_secondary.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 9. Specify Secondary Target


The Secondary Target step of the wizard is available if you have enabled the Configure secondary destinations for this job option at the Storage step of the wizard.

At the Secondary Target step of the wizard, you can link the Veeam Agent backup job managed by the backup server to a backup to tape or backup copy job. As a result, the backup job will be added as a source to the backup to tape or backup copy job. Backup files created with the backup job will be archived to tape or copied to the secondary backup repository according to the secondary jobs schedule. For more information, see [Linking Backup Jobs to Backup Copy Jobs](linking_backup_to_copy.md) and [Linking Backup Jobs to Backup to Tape Jobs](linking_backup_to_backup_to_tape.md).

The backup to tape job or backup copy job must be configured beforehand. You can create these jobs with an empty source. When you link the Veeam Agent backup job to these jobs, Veeam Backup & Replication will automatically update the linked jobs to define the Veeam Agent backup job as a source for these jobs.

To link a backup to tape or backup copy job:

1. At the Secondary Target step of the wizard, click Add.
2. From the jobs list, select a backup to tape or backup copy job that must be linked to the Veeam Agent backup job. You can link several jobs to the backup job — for example, one backup to tape job and one backup copy job. To quickly find the job, use the search field at the bottom of the wizard.

![Step 9. Specify Secondary Target](images/agent_job_secondary_unix.webp)

Page updated 2026-06-19

