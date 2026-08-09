---
title: "Viewing Job Session Results"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/session_results_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Viewing Job Session Results


To view the detailed statistics for a specific job session, open the backup job details and click the necessary session in the History box. For more information on the backup job details, see [Viewing Backup Job Details](realtime_statistics_web.md).

Statistics Counters

Veeam Backup & Replication displays backup job statistics for the following counters:

* The History box shows a recent activity timeline of your backup job. Each dot represents a job run on the displayed date: a green dot indicates a successful run, an orange dot indicates a run that finished with a warning, and a red dot indicates a run that finished with an error. Use the Show filter to display all runs, or only those that finished with the success, warning, or error status.

* The Protection Overview box indicates the percentage of protected workloads in the last job run and shows how many workloads finished with the Success, Warnings and Errors statuses.

* The Session Details box shows the list of actions performed.

* The Job View tab in the upper-right corner shows a list of operations performed during the job. To see a list of operations for a specific object included in the job, click the object in the pane on the left. To see a list of operations for the entire job, click anywhere on the blank area in the left pane.
* The Workload View tab in the upper-right corner shows a list of objects processed by the job.
* The Status box shows information about the job results. This box informs how many tasks have been completed with the Success, Warning and Failed statuses (one task per one VM).

* Success — the task is completed successfully.
* Warning — the task is completed with minor errors. Depending on the nature of the errors, the backup data may not be consistent.
* Failed — the task is not completed due to a blocking error.

* The Job Session Results box shows general information about the job:

* Duration — time from the job start till the current moment or job end.
* Bottleneck — a bottleneck in the data transmission process. To learn about job bottlenecks, see [Performance Bottlenecks](detecting_bottlenecks.md).
* Processing rate — average speed of VM data processing. This counter is a ratio between the amount of data actually read and the time it took to process the data. Note that only the data transfer time is used for the calculation, and the job's runtime is irrelevant.
* Read — the amount of data read from the datastore by the source-side [Veeam Data Mover](veeam_transport_service.md) prior to applying compression and deduplication. For incremental job runs, the value of this counter is typically lower than the value of the Processed counter. Veeam Backup & Replication reads only data blocks that have changed since the last job session, processes and copies these data blocks to the target.
* Processed — total size of all VM disks processed by the job.
* Transferred — the amount of data transferred from the source-side Veeam Data Mover to the target-side Veeam Data Mover after applying compression and deduplication. This counter does not directly indicate the size of the resulting files. Depending on the backup infrastructure and job settings, Veeam Backup & Replication can perform additional activities with data: deduplicate data, decompress data prior to writing the file to disk, and so on. The activities can impact the size of the resulting file.

Colored Graph

To visualize the backup job progress, Veeam Backup & Replication displays a colored graph in the Throughput box:

* The light blue Processed line defines the amount of processed data.
* The dark blue Transferred line defines the amount of data transferred from the source-side Veeam Data Mover to the target-side Veeam Data Mover.

If the job session is still running, you can click the colored graph to view the data rate for the last 5 minutes or the whole processing period. If the job session has already ended, the graph displays information for the whole processing period only. The graph is displayed only for the currently running job session or the latest job session. If you select a session other than the latest one, the colored graph will not be displayed.[![Viewing Job Session Results](images/session_stats_web.webp)](images/session_stats_web.webp)

Page updated 2026-07-21

