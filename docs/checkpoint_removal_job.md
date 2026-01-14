---
title: "Background Checkpoint Removal Job"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/checkpoint_removal_job.html"
last_updated: "12/2/2024"
product_version: "13.0.1.1071"
---

# Background Checkpoint Removal Job

In this article

To improve the performance of backup jobs that target object storage repositories, Veeam Backup & Replication runs a background checkpoint removal job. This job runs continuously as a background activity and removes checkpoints from backups located in object storage repositories.

How Background Checkpoint Removal Job Works

The algorithm of the background checkpoint removal job depends on the type of backup. For most backups, Veeam Backup & Replication removes outdated checkpoints at the [request of the job](#standard) or [when the checkpoints removal job restarts](#jobrestart).

Deleting Checkpoints by Job Request

The checkpoint removal by the job request has the following algorithm:

1. A job produces a backup and starts to process this backup.
2. The job sends a request to a backup service to remove outdated checkpoints and continues to run without waiting for a response from the service. By default, the background checkpoint removal job periodically checks the backup service for requests to remove checkpoints. Once it gets the request, it starts the removal.
3. The background checkpoint removal job gets the backup ID, host ID, and repository ID from the request.
4. The background checkpoint removal job starts an agent to get a list of outdated checkpoints.

|  |
| --- |
| Note |
| To reduce the load on the backup server, Veeam Backup & Replication starts agents for checkpoint removal on different hosts depending on the repository connection mode:   * For direct connection mode the agent starts on the mount server. * For gateway server connection mode the agent starts on the gateway server configured for the object storage repository. |

1. The background checkpoint removal job deletes outdated checkpoints.

Deleting Checkpoints when Background Checkpoint Removal Job Starts

To delete outdated checkpoints when the background checkpoint removal job restarts, Veeam Backup & Replication applies the backup filtering algorithm. It compares the latest removed checkpoint with the latest checkpoint created by the job. If the latest removed checkpoint does not coincide with the latest created checkpoint, Veeam Backup & Replication identifies the outdated checkpoint and removes it. Otherwise, the checkpoint removal is skipped.

|  |
| --- |
| Note |
| The filtering algorithm processes backups based on their type and repository connection mode:   * For backups created by Veeam Agent jobs that operate in managed by agent or standalone mode and directly access object storage repositories, the background checkpoint removal job deletes outdated checkpoints every time it restarts. * The background checkpoint removal job on every restart skips from processing the following types of backups:  * Backups created by VM jobs. * Backups created by Veeam Agent jobs managed by Veeam Backup & Replication * Backups created by Veeam Agent jobs that operate in managed by agent or standalone mode that use a gateway server to connect to object storage repositories. |

Cloud Connect Checkpoints Removal

Depending on the backup type and repository connection mode, Veeam Backup & Replication deletes checkpoints either on the tenant or on the Service provider side:

* Backups created by any job or Veeam Agent managed by Veeam Backup & Replication jobs that directly access object storage repositories: checkpoints are deleted on the tenant side by the job request.
* Backups created by any job or Veeam Agent jobs managed by Veeam Backup & Replication that use a gateway server to connect to object storage repositories: checkpoints are deleted on the Service provider side by job request.
* Backups created by Veeam Agent jobs managed by agent or in a standalone mode that connect to the object storage directly or using a gateway server: checkpoints are deleted on the Service provider every time the checkpoint removal job restarts.

Email Reports

Veeam Backup & Replication generates an email report that includes errors from all completed checkpoint removal jobs. The report is sent once a day according to [Global Email Notification Settings](general_email_notifications.md).

Page updated 12/2/2024

Page content applies to build 13.0.1.1071
