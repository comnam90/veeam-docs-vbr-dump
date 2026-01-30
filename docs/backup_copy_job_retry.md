---
title: "Automatic Job Retries"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_job_retry.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Automatic Job Retries


Veeam Backup & Replication automatically retries several operations that are performed within a backup copy job session.

Periodic Backup Copy Job Tasks Retry

By default, in the periodic copy mode, Veeam Backup & Replication automatically retries a failed backup copy task 5 times within one backup copy job session. A new task is started immediately after the previous one.

The backup copy task is retried only if the previous task has failed and a restore point has not been copied to the target backup repository. Veeam Backup & Replication does not perform a retry if a task has finished with the Success or the Warning status.

The backup copy task is retried during the same backup copy session only. If a restore point fails to be copied during all retries in the current backup copy session, Veeam Backup & Replication marks the current task as failed. [For the legacy periodic mode] After that, Veeam Backup & Replication performs the necessary transformation processes and starts a new backup copy session.

A backup copy job can process several machines. If only some machines are successfully processed by the backup copy task, Veeam Backup & Replication creates a restore point holding data for these machines in the target backup repository. Veeam Backup & Replication will attempt to process restore points for all machines during the next backup copy session.

|  |
| --- |
| Note |
| Some errors from WAN accelerators can block backup copy job retries. For example, if there is no space in the global cache on the target WAN accelerator, Veeam Backup & Replication puts backup copy operations on hold and waits for the expiration of the backup copy session. |

Immediate Backup Copy Job Retry

By default, in the immediate copy mode, Veeam Backup & Replication automatically retries a failed backup copy job 3 times. Instead of retrying each task within one backup copy job session, Veeam Backup & Replication performs each retry as a separate session run.

If no new restore points are available, Veeam Backup & Replication performs retries at 1 hour interval. If new restore points are available, Veeam Backup & Replication performs retries immediately.

Transformation Retry

After the backup copying task, Veeam Backup & Replication may perform a number of additional transformation processes in the target backup repository. These processes include the backup chain transformation, removing of deleted machines from restore points and compacting a full backup file. For more information, see [Transformation Processes](backup_copy_transform_operations.md).

Veeam Backup & Replication may fail to perform transformation: for example, if the backup file in the target backup repository is locked by the file-level restore session. By default, Veeam Backup & Replication automatically retries transformation processes for 5 times. The first interval between retries is 1 minute; the interval doubles with every new attempt. If all retries of transformation processes fail, Veeam Backup & Replication does the following:

* [For the immediate copy mode] Stops the job with the Fail status and waits for the new job session.
* [For the periodic copy mode] Stops the job with the Fail status and waits for the job to retry according to schedule.

Virtual Infrastructure Access Retry

At the beginning of every backup copy session, Veeam Backup & Replication accesses the virtual infrastructure to make up a list of machines processed by the job.

Veeam Backup & Replication may fail to access the virtual infrastructure for some reason: for example, in case the vCenter Server or the Hyper-V host is not responding. By default, Veeam Backup & Replication automatically retries access operations for 5 times with a 5 minute interval.


