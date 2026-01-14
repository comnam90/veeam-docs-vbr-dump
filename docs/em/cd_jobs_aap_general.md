---
title: "cd_jobs_aap_general"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/cd_jobs_aap_general.html"
last_updated: "9/4/2025"
product_version: "13.0.1.1071"
---


In this article

On the General tab, you can specify general application-aware processing settings.

1. In the Applications section, select the option that corresponds to your transactionally-consistent backup creation scenario.

* Select Require successful processing (default option) if you want Veeam Backup & Replication to stop the backup job if an error occurs.
* Select Try application processing, but ignore failures if you want to continue the backup process even if an error occurs. This option guarantees completion of the job. The created backup image will not be transactionally consistent, but rather crash-consistent.
* Select Disable application processing if you do not want to enable application-aware processing for the VM. This option makes the Transaction Logs Processing section unavailable.

1. [For Microsoft Exchange, Microsoft SQL Server, Oracle and PostgreSQL] In the Transaction Logs Processing section, specify whether this job should process transaction logs upon a successful backup.

* Select Process transaction logs with this job if you want Veeam Backup & Replication to process transaction logs.

[For Microsoft Exchange] With this option selected, the non-persistent runtime components or persistent components running on the VM guest OS will wait for backup to complete successfully and then trigger truncation of transaction logs. If the backup job fails, the logs will remain untouched on the VM guest OS until the next start of the non-persistent runtime components or persistent components.

[For Microsoft SQL Server, Oracle and PostgreSQL] Specify settings for transaction log handling:

* For Microsoft SQL Server transaction log processing — on the SQL tab. For more information, see [Microsoft SQL Server Transaction Log Settings](cd_jobs_aap_sql.md).
* For Oracle database archived logs processing — on the Oracle tab. For more information, see [Oracle Archived Log Settings](cd_jobs_aap_oracle.md).
* For PostgreSQL database archive logs processing — on the PostgreSQL tab. For more information, see [PostgreSQL Archive Log Settings](cd_jobs_aap_postgresql.md).

* Select Perform copy only if you want to use native application means or a third-party tool to process transaction logs. Veeam Backup & Replication will create a copy-only backup for the selected machine. The copy-only backup preserves a chain of full/differential backup files and transaction logs, so Veeam Backup & Replication will not trigger transaction log truncation. This option is recommended if you are using another backup tool to perform the machine guest-level backup, and this tool maintains consistency of the database state. To learn more, see the [Guest Processing](https://helpcenter.veeam.com/docs/vbr/userguide/guest_processing.html?ver=13) section of the Veeam Backup & Replication User Guide.

With this option selected, the SQL, Oracle and PostgreSQL tabs are not available.

1. In the Persistent guest agent section, specify if Veeam Backup & Replication must use persistent guest agents on each protected VM for application-aware processing.

By default, Veeam Backup & Replication uses non-persistent runtime components. Veeam Backup & Replication deploys runtime components on each protected VM when the backup job starts, and removes the runtime components as soon as the backup job finishes.

Select the Use persistent guest agent check box to enable persistent agent components for guest processing. For more information, see the [Non-Persistent Runtime Components and Persistent Agent Components](https://helpcenter.veeam.com/docs/vbr/userguide/runtime_process.html?ver=13) section of the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| If both Microsoft SQL Server and Oracle Server are installed on the same VM, and this VM is processed by a job with log backup enabled for both applications, Veeam Backup & Replication will back up only Oracle transaction logs. Microsoft SQL Server transaction logs will not be processed. |

![General Settings](images/em_edit_job_aaip_general.webp "General Settings")

Page updated 9/4/2025

Page content applies to build 13.0.1.1071
