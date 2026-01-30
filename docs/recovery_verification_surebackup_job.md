---
title: "Using SureBackup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/recovery_verification_surebackup_job.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Using SureBackup


A SureBackup job is a task for recovery verification. You can run the SureBackup job manually or schedule it to run automatically.

SureBackup job can operate in two different backup verification modes:

* Full recoverability testing. Veeam Backup & Replication runs machines in an isolated environment directly from backup and performs tests against live applications.This mode ensures recoverability of your production workloads in a disaster recovery event. To learn more, see [Full Recoverability Testing](surebackup_hiw.md).
* Backup verification and content scan only. Veeam Backup & Replication performs backup integrity check and its content analysis to detect traces of malware or any other unwanted or sensitive data. These tests do no require setting up a virtual lab or an application group. To learn more, see [Backup verification and content scan only](https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_hiw.html?ver=13#backup-verification-and-content-scan-only).

Getting Started

Before you configure a SureBackup job that will test your backup, you must complete the following steps:

1. Consider limitations listed in section [Recovery Verification for Veeam Agent Backups](agents_recovery_verification.md#cluster_limitations).
2. Prepare a backup that you will test using the SureBackup job:

|  |
| --- |
| IMPORTANT |
| [For Microsoft Windows computers] If the backup that you test with the SureBackup job contains pending updates, the Veeam Agent computer may start rebooting while the SureBackup job is running, and the job will fail. |

1. Add a computer to the inventory and deploy Veeam Agent on this computer using the Veeam Backup & Replication console. To learn more, see [Creating Protection Groups](https://helpcenter.veeam.com/docs/backup/agents/protection_group_add.html?ver=120).
2. Create a backup job. To learn more, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).
3. Run the backup job to create a backup.

1. [For full recoverability testing mode] Configure the backup infrastructure to create the SureBackup job:

1. Add a virtual lab. The virtual lab is an isolated virtual environment in which Veeam Backup & Replication will test your backups. VMware vSphere and Microsoft Hyper-V servers are supported. To learn more, see [Creating Virtual Lab](create_vlab.md).

|  |
| --- |
| TIP |
| You can add a virtual lab during creating a SureBackup job at the [Virtual Lab](surebackup_job_create.md#lab_12.1) step of the New SureBackup Job wizard. |

1. Add an application group. The application group provides a fully functional work for a host or a group of hosts that is created by Veeam Agent to test your backup. To learn more, see [Creating Application Groups](appgroup_create.md) section.

When you configure the application group, you must add the backup you want to test to this group.

|  |
| --- |
| TIP |
| Consider the following:   * You can add an application group during creating a SureBackup job at the [Application Group](surebackup_job_create.md#group_12.1) step of the New SureBackup Job wizard. * The application group is optional for the SureBackup job. If you do not create an application group, you can still use a backup job as a source of backups for the SureBackup job. In this case the SureBackup job will test all Veeam Agent backups created by this backup job. To learn more, see [Creating SureBackup Job](surebackup_job_create.md). |

After all preparations are done, you can [create the SureBackup job](surebackup_job_create.md).


