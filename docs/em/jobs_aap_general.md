---
title: "General Settings"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/jobs_aap_general.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# General Settings


On the General tab, you can specify general application-aware processing settings.

1. In the Applications section, select the option that corresponds to your transactionally-consistent backup creation scenario.

* Select Require successful processing (default option) if you want Veeam Backup & Replication to stop the backup job if an error occurs.
* Select Try application processing, but ignore failures if you want to continue the backup process even if an error occurs. This option guarantees completion of the job. The created backup image will not be transactionally consistent, but rather crash-consistent.
* Select Disable application processing if you do not want to enable application-aware processing for the VM. This option makes the Transaction Logs Processing section unavailable.

1. If you want Veeam Backup & Replication to process application logs or create copy-only backups, do one of the following:

* [For Microsoft Exchange and Microsoft SQL VMs] If you want Veeam Backup & Replication to process application logs, select Process transaction logs with this job and specify settings on the SQL tab. For more information, see [Microsoft SQL Server Transaction Log Settings](jobs_aap_sql.md).

|  |
| --- |
| Note |
| [For Microsoft Exchange VMs] If you select this option, Veeam Backup & Replication will back up the Exchange database and its logs. The non-persistent runtime components or persistent components that run on the VM guest OS will wait for a backup job to complete successfully. After that, they will trigger truncation of transaction logs on a Microsoft Exchange server. If the backup job fails, the logs on this server will remain untouched. |

* [For Microsoft Exchange and Microsoft SQL VMs] If you use a third-party backup tool to perform VM guest level backup, and this tool maintains consistency of the database state, select Perform copy only. Veeam Backup & Replication will create a copy-only backup for the selected VM. The copy-only backup preserves the chain of full or differential backup files and transaction logs on the VM. For more information, see [Microsoft Docs](http://msdn.microsoft.com/en-us/library/ms191495.aspx).

Note that if you select this option, the SQL tab will not be available in the VM Processing Settings window.

* [For Oracle VMs and PostgreSQL VMs] You must specify settings for application log handling on the Oracle and PostgreSQL tabs of the VM Processing Settings window. For more information, see [Oracle Archived Redo Log Settings](jobs_aap_oracle.md) and [PostgreSQL Archive Log Settings](jobs_aap_postgresql.md).

1. In the Persistent guest agent section, specify if Veeam Backup & Replication must use persistent guest agents on each protected VM for application-aware processing.

By default, Veeam Backup & Replication uses non-persistent runtime components. Veeam Backup & Replication deploys runtime components on each protected VM when the backup job starts, and removes the runtime components as soon as the backup job finishes.

Select the Use persistent guest agent check box to enable persistent agent components for guest processing. For more information, see the [Non-Persistent Runtime Components and Persistent Agent Components](https://helpcenter.veeam.com/docs/vbr/userguide/runtime_process.html?ver=13) section of the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| If both Microsoft SQL Server and Oracle Server are installed on the same VM, and this VM is processed by a job with log backup enabled for both applications, Veeam Backup & Replication will back up only Oracle transaction logs. Microsoft SQL Server transaction logs will not be processed. |

![General Settings](images/em_edit_job_aaip_general.webp "General Settings")


