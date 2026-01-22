---
title: "Step 5. Link Backup or Replication Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_job_joblink_vm.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Step 5. Link Backup or Replication Job


At the Linked Jobs step of the wizard, select backup or replication jobs with machines that you want to verify with the SureBackup job.

You can link a backup or replication job to the SureBackup job or skip this step. If you do not link a backup or replication job, in Full recoverability testing mode Veeam Backup & Replication will only start machines from the application group in the virtual lab and verify them. You have an option not to link a backup or replication job to the SureBackup job only if you have selected an application group at the [Application Group](surebackup_job_appgroup_vm.md) step of the wizard.

|  |
| --- |
| Note |
| You cannot link backup copy jobs to the SureBackup job. |

Linking Backup or Replication Job

To link a backup or replication job to the SureBackup job:

1. [For full recoverability testing mode] Select the Test backups of the following backup jobs check box.
2. Click Add.
3. In the Select Jobs window, select backup and replication jobs.
4. In the Process simultaneously up to … machines field, specify the maximum number of machines (from a linked job) that can be started at the same time. For example, if you select to start three machines at the same time, Veeam Backup & Replication will create three streams — one stream per every verified machine. All three machines will be tested together. But if you select to start one machine, then only one machine will been tested and powered off, and the next machine will be started in the available stream. In Full recoverability testing mode, after all machines are verified, machines from the application group will be powered off or will be left running (if the Keep the application group running after the job completes option has been enabled at the [Application Group](surebackup_job_appgroup_vm.md) step of the wizard).
5. Select Process only randomly selected ... machines during each run check box and specify the maximum number of machines you want to randomly test.

To exclude objects from the SureBackup job, perform the following steps:

1. Click Exclusions.
2. Click Add and select one of the following source options:

* From jobs.
* From backups.

1. In the Select Objects window, select objects that you want to exclude and click Add.

For the From jobs option, you can select the Show full hierarchy check box to display the hierarchy of all hosts added to Veeam Backup & Replication.

1. Click OK.

To remove an object from the list, select it and click Remove.

|  |
| --- |
| Note |
| Removed or deleted machines can be excluded from the SureBackup job using the From backups option. |

![Step 5. Link Backup or Replication Job](images/surebackup_job_link_121.webp)


