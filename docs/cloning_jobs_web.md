---
title: "Cloning Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cloning_jobs_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Cloning Jobs


You can create new jobs using job cloning. Job cloning allows you to create an exact copy of any job with the same job settings. Configuration information of the created job copy is written to the configuration database that stores information about the original job.

To create multiple jobs with similar settings, you can configure a set of jobs that will be used as "job templates". You can then clone these "job templates" and edit the settings of cloned jobs as required.

The name of the cloned job is formed by the following rule: <job\_name\_clone1>, where job\_name is the name of the original job and clone1 is a suffix added to the original job name. If you clone the same job again, the number in the name will be increased, for example, job\_name\_clone2, job\_name\_clone3, and so on.

When cloning a job, Veeam Backup & Replication can change some job settings so that cloned jobs do not hinder original jobs.

* If the original job is scheduled to run automatically, Veeam Backup & Replication disables the cloned job. To enable the cloned job, select it in the job list and click Manage > Disable on the ribbon or right-click the job and select Manage > Disable.
* If the original job is configured to use a secondary target, the cloned job is created without the secondary target settings.

To clone a job:

1. In the management pane, click the Jobs node.
2. In the working area, select a job and click Manage > Clone on the ribbon or right-click the job and select Manage > Clone.
3. After a job is cloned, you can edit all its settings, including the job name.

[![Click to zoom in](images/cloning_jobs_web.webp)](images/cloning_jobs_web.webp "Click to zoom in")

Page updated 2026-06-18

