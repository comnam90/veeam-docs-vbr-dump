---
title: "cdp_aap_general"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/cdp_aap_general.html"
last_updated: "9/4/2025"
product_version: "13.0.1.1071"
---


In this article

On the General tab, you can specify general application-aware processing settings.

1. In the Applications section, select the option that corresponds to your transactionally-consistent backup creation scenario.

* Select Require successful processing (default option) if you want Veeam Backup & Replication to stop the CDP replication if an error occurs.
* Select Try application processing, but ignore failures if you want to continue the CDP replication even if an error occurs. This option guarantees the CDP policy will continue working. The created replica will not be transactionally consistent, but rather crash consistent.
* Select Disable application processing if you do not want to enable application-aware processing for the VM. This option makes the Transaction Logs Processing section unavailable.

1. [For Microsoft Exchange, Microsoft SQL Server, and Oracle] In the Microsoft VSS section, specify whether this CDP policy should process transaction logs or create copy-only replicas.

* Select Process transaction logs with this job if you want Veeam Backup & Replication to process transaction logs.

[For Microsoft Exchange] Transaction logs will be truncated after the CDP policy creates a long-term restore point. If the creation fails, the logs will remain untouched until the next start of the long-term restore point creation.

[For Microsoft SQL Server, Oracle] Specify settings for transaction log handling:

* For Microsoft SQL Server transaction log processing — on the SQL tab. For more information, see [Microsoft SQL Server Transaction Log Settings](cdp_aap_sql.md).
* For Oracle database archived logs processing — on the Oracle tab. For more information, see [Oracle Archived Log Settings](cdp_aap_oracle.md).

* Select Perform copy only if you use another replication tool to perform guest level replication, and this tool maintains consistency of the database state. Veeam Backup & Replication will create a copy-only replica for the selected VM. The copy-only replica preserves the chain of full and differential backup files and transaction logs on the VM. For more information, see [Microsoft Docs](http://msdn.microsoft.com/en-us/library/ms191495.aspx).

With this option selected, the SQL, Oracle and PostgreSQL tabs are not available.

1. In the Persistent guest agent section, specify if Veeam Backup & Replication must use persistent guest agents on the VM for application-aware processing.

By default, Veeam Backup & Replication uses non-persistent runtime components. Veeam Backup & Replication deploys runtime components on each protected VM when the backup job starts, and removes the runtime components as soon as the backup job finishes.

Select Use persistent guest agent to enable persistent agent components for guest processing. For more information, see the [Non-Persistent Runtime Components and Persistent Agent Components](https://helpcenter.veeam.com/docs/vbr/userguide/runtime_process.html?ver=13) section of the Veeam Backup & Replication User Guide.

![General Settings](images/em_cdp_policies_edit_aaip_general.webp "General Settings")

Page updated 9/4/2025

Page content applies to build 13.0.1.1071
