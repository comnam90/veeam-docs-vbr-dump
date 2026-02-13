---
title: "Cloning Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_backup_job_clone.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Cloning Backup Jobs


You can create a new job by cloning an existing one. Job cloning allows you to create an exact copy of any job with the same job settings.

To clone a job, do the following:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the necessary job and click Clone on the ribbon.

Alternatively, right-click the job and select Clone.

The name of the cloned job is formed by the following rule: <job\_name\_clone1>, where job\_name is the name of the original job and clone1 is a suffix added to the original job name. If you clone the same job again, the number in the name will be incremented, for example, job\_name\_clone2, job\_name\_clone3 and so on. To change the name of a cloned job, edit the job as described in section [Editing Backup Job Settings](sch_backup_job_edit.md).

|  |
| --- |
| Note |
| If the original job is scheduled to run automatically, Veeam Plug-in for Scale Computing HyperCore disables the cloned job. To enable the cloned job, select it in the job list and click Enable. |

[![Cloning Job](images/sch_backup_job_clone.webp)](images/sch_backup_job_clone.webp "Cloning Job")


