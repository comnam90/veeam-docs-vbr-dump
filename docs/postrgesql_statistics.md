---
title: "WAL Backup Statistics"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/postrgesql_statistics.html"
last_updated: "11/12/2025"
product_version: "13.0.1.1071"
---

# WAL Backup Statistics


You can view the statistics of the WAL files backup job in the History view or in the Home view in Veeam Backup & Replication.

In the statistics window, you can examine the overall statistics for WAL files and view per-VM information.

In the upper part of the statistics window, Veeam Backup & Replication displays information about the WAL files backup job for all VMs included in the parent backup job.

The Last period (all VMs) section contains statistics data for the selected session of the backup job.

In the Databases column, you can view the following information:

* Protected — number of instances that were backed up at least once during the last session.
* Unprotected — number of instances that failed to be backed up during the last session.
* Excluded — instances excluded from processing. Instances may be excluded for the following reasons:

+ Archive\_mode is turned off for the database.

+ The database was deleted after the latest full backup.
+ The database was added to the list of exclusions.

|  |
| --- |
| Note |
| Unprotected instances do not comprise Excluded instances, as they have different reasons for being non-processed. |

In the RPO column, you can view the following information:

* SLA — how many log backup intervals were completed in time with successful log backup (calculated as a percentage of the total number of intervals).
* Misses — how many intervals failed to complete in time with successful log backup (number of intervals).
* Max delay — difference between the configured log backup interval and the time actually required for log backup. If exceeded, a warning is issued.

In the Status column, the following information is displayed (per job): number of VMs processed successfully, with warnings or with errors.

The Last session section displays the following information for the latest log processing interval for the selected VM:

* Duration — duration of log shipment from the VM guest OS to the backup repository since the current log processing interval has started.
* Bottleneck — operation with the greatest duration in the last completed interval. The operation may have the following bottlenecks:

| Display Name | Slowing-down Operation |
| --- | --- |
| Log backup | Saving archived log files to a temporary location on VM guest OS (to work around, see the Veeam KB article: [this Veeam KB article](https://www.veeam.com/kb2093)) |
| Network | Uploading log files to the log shipping server |
| Target | Saving files to the target repository |

* Read — amount of data read from the temporary folder on VM guest OS.
* Transferred — amount of data transferred to the target repository.

The Last period section displays the following statistics of log backups for every VM for the latest session of the log backup job:

* The RPO column displays statistics on log processing interval.
* The Sessions column includes statistics of log backups per VM, calculated based on their status:

+ Success — number of intervals when all database logs were backed up successfully
+ Warning — number of sequential intervals with failed log processing (if not more than 4 intervals in a sequence)
+ Errors — number of sequential intervals with failed log processing (more than 4 intervals in a sequence)

* The Duration column includes the following information:

+ Average — average duration of log data transfer (through all intervals in the session)
+ Maximum — maximal duration of log data transfer (through all intervals in the session)
+ Sync interval — duration of periodic intervals specified for log backup in the parent job settings (default is 15 min)

* The Log size column displays the following information:

+ Average — average amount of data read from the VM guest OS through all intervals
+ Maximum — maximal amount of data read from the VM guest OS over all intervals
+ Total — total amount of data written to the backup repository

The pane at the bottom shows all actions performed during the job run. To filter out actions with a certain status, use the Errors, Warnings and Success buttons.

|  |
| --- |
| Note |
| Statistics on WAL files processing is updated periodically, simultaneously for the VM backup job (parent) and WAL files backup job (child job). |


