---
title: "SureBackup Job for VM Replicas"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surereplica_job.html"
last_updated: "8/20/2024"
product_version: "13.0.1.1071"
---

# SureBackup Job for VM Replicas

In this article

You can verify VM replicas with the SureBackup job only in the Full recoverability testing mode. The SureBackup job aggregates all settings and policies of a recovery verification task, such as application group and virtual lab to be used, VM replicas that must be verified in the virtual lab and so on. The SureBackup job can be run manually or scheduled to be performed automatically.

When a SureBackup job runs, Veeam Backup & Replication first creates an environment for VM replica verification:

1. If antivirus software scan is enabled, Veeam Backup & Replication performs antivirus scan and use backup server as the mount server during this operation.
2. Veeam Backup & Replication starts the virtual lab.
3. In the virtual lab, it starts VMs from the application group or the linked job in the required order. VMs remain running until the verified VM replicas are booted and tested. If Veeam Backup & Replication does not find a successful VM replica or backup for any of VMs from the application group, the SureBackup job will fail.

When the virtual lab is ready, Veeam Backup & Replication starts VM replicas from the necessary restore point, tests and, depending on the specified settings, verifies them one by one or creates several streams and tests VM replicas simultaneously. If Veeam Backup & Replication does not find a successful restore point for any of verified VM replicas, verification of this VM replica fails, but the job continues to run.

By default, you can start and test up to three VM replicas at the same time. You can also increase the number of VMs to be started and tested simultaneously. Keep in mind that if these VMs are resource demanding, performance of the SureBackup job may decrease.

When the verification process is complete, VMs from the application group are powered off. Optionally, you can leave the VMs from the application group running to perform manual testing or enable user-directed application item-level recovery.

In some cases, the SureBackup job schedule may overlap the schedule of the replication job linked to it. The VM replica files may be locked by the replication job and the SureBackup job will be unable to verify such replica. In this situation, Veeam Backup & Replication will not start the SureBackup job until the replication job is over.

To overcome the situation of job overlapping, you may chain the replication and SureBackup jobs or define the timeout period for the SureBackup job. For more information, see [Specifying Job Schedule](surebackup_job_schedule_vm.md).

|  |
| --- |
| Note |
| You can mix VM backups and replicas in the recovery verification job. For example, the application group may contain VMs that will be started from backup files and the job linked to the recovery verification job may be a replication job. Veeam Backup & Replication supports any type of a mixed scenario. Note that VMs that you verify with a SureBackup job must belong to the same platform — VMware or Hyper-V. |

Related Topis

[SureBackup Job for VM Replicas Processing](surereplica_job_processing.md)

Page updated 8/20/2024

Page content applies to build 13.0.1.1071
