---
title: "Cloning Backup Copy Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cloning_backup_copy_job.html"
last_updated: "8/31/2025"
product_version: "13.0.1.1071"
---

# Cloning Backup Copy Job


You can create new backup copy jobs by means of job cloning. Job cloning allows you to create an exact copy of any job with the same job settings. Configuration information of the created job copy are written to the configuration database that stores information of the original job.

To create multiple jobs with similar settings, you can configure a set of jobs that will be used as ‘job templates’. You can then clone these 'job templates' and edit settings of cloned jobs as required.

The name of the cloned job is formed by the following rule: <job\_name\_clone1>, where job\_name is the name of the original job and clone1 is a suffix added to the original job name. If you clone the same job again, the number in the name will be incremented, for example, job\_name\_clone2, job\_name\_clone3 and so on.

When cloning job, Veeam Backup & Replication can change some job settings so that cloned jobs do not hinder original jobs.

* If the original job is scheduled to run automatically, Veeam Backup & Replication disables the cloned job. To enable the cloned job, select it in the job list and click Disable on the ribbon or right-click the job and select Disable.
* If the original job is configured to use a secondary target, the cloned job is created without the secondary target settings.

To clone a job:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the backup copy job and click Clone on the ribbon or right-click the job and select Clone.
4. After a job is cloned, you can edit all its settings, including the job name.

[![Cloning Backup Copy Job](images/backup_copy_cloning.webp)](images/backup_copy_cloning.webp)


