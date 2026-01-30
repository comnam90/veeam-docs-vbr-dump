---
title: "SureBackup Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_job_hv.html"
last_updated: "5/5/2025"
product_version: "13.0.1.1071"
---

# SureBackup Job


A SureBackup job is a task for recovery verification. The SureBackup job can run in two different modes: Full recoverability testing and Backup verification and content scan only.

In the Full recoverability testing mode, the SureBackup job aggregates all settings and policies of the recovery verification task such as application group and virtual lab to be used, machine backups that must be verified in the virtual lab, and so on. It runs machines in an isolated environment directly from backup and performs tests against live applications.This mode ensures recoverability of your production workloads in a disaster recovery event.

In the Backup verification and content scan only mode, the SureBackup job performs only backup integrity check and its content analysis to detect traces of malware or any other unwanted or sensitive data. These tests do no require setting up a virtual lab or an application group.

You can run the SureBackup job manually or schedule it to run automatically.

When a SureBackup job runs in the Full recoverability testing mode, Veeam Backup & Replication first creates an environment for recovery verification:

1. Veeam Backup & Replication starts the virtual lab.
2. In the virtual lab, Veeam Backup & Replication starts machines from the application group in the required order. Machines from the application group remain running until verified machines (machines from the linked job) are booted from backups and tested.

If Veeam Backup & Replication does not find a valid restore point for any of the machines from the application group, the SureBackup job fails.

1. When the virtual lab is ready, Veeam Backup & Replication starts verified machines to the necessary restore point and, depending on the job settings, verifies them one by one or creates several streams and verifies a number of machines simultaneously.

If Veeam Backup & Replication does not find a valid restore point for any of the verified machines, verification of this machine fails, but the job continues to run.

By default, you can start and test up to three machines at the same time. You can also increase the number of machines to be started and tested simultaneously. Keep in mind that if these machines are resource demanding, performance of the SureBackup job as well as performance of the Hyper-V host on which the virtual lab resides may decrease.

Once the verification process is complete, machines from the application group are powered off. Optionally, you can leave machines from the application group running to perform manual verification or enable user-directed application item-level recovery.

In some cases, the SureBackup job schedule may overlap the schedule of the backup job linked to it. The backup file may be locked by the backup job and the SureBackup job will be unable to verify such backup. In this situation, Veeam Backup & Replication will not start the SureBackup job until the backup job is over.

To overcome the situation of job overlapping, you may chain the backup and SureBackup jobs or define the timeout period for the SureBackup job. For more information, see [Specifying Job Schedule](surebackup_job_schedule_hv.md).

Related Topics

* [SureBackup Job Processing](surebackup_job_processing.md)
* [Creating SureBackup Job](create_surebackupjob_hv.md)
* [Starting and Stopping SureBackup Job](surebackup_job_start.md)
* [Viewing Recovery Verification Job Statistics](viewing_surebackup_stats.md)
* [Creating SureBackup Session Reports](creating_surebackup_reports.md)


