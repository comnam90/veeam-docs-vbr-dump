---
title: "Cloning Log Backup Jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_clone_job.html"
last_updated: "8/8/2025"
product_version: "13.0.1.1071"
---

# Cloning Log Backup Jobs

In this article

This option is available only for log backups.

You can create a new job by cloning an existing one. Job cloning allows you to create an exact copy of any job with the same job settings.

The name of the cloned job is formed by the following rule: <job\_name\_clone1>, where job\_name is the name of the original job and clone1 is a suffix added to the original job name. If you clone the same job again, the number in the name will be incremented, for example, job\_name\_clone2, job\_name\_clone3, and so on. To change the name of a cloned job, edit the job as described in [Editing Backup Job Settings](entra_id_edit_job_setting.md).

Considerations

When cloning a job, Veeam Backup & Replication can change some job settings so that cloned jobs do not hinder original jobs.

* If the original job is scheduled to run automatically, Veeam Backup & Replication disables the cloned job. To enable the cloned job, select it in the job list and click Disable on the ribbon or right-click the job and select Disable.
* If the original job is configured to use a secondary target, Veeam Backup & Replication also clones the copy job.

Cloning Job

To clone a log backup job:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the job and click Clone on the ribbon. Alternatively, right-click the job and select Clone.

After a job is cloned, you can edit all its settings, including the job name.

[![Clone Entra ID Log Job](images/entra_id_clone_job.webp)](images/entra_id_clone_job.webp "Clone Entra ID Log Job")

Page updated 8/8/2025

Page content applies to build 13.0.1.1071
