---
title: "Application Item Restore"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_backup_restore_app_items.html"
last_updated: "4/9/2025"
product_version: "13.0.1.1071"
---

# Application Item Restore


Veeam Backup Enterprise Manager supports item-level recovery from backups or replicas. These backups and replicas must be created with enabled application-aware processing. To restore a database to its specific point in time, choose the backups (or replicas) created by a job that processes database logs. For more information, see [Application-Aware Processing](em_edit_job_aaip_settings.md).

You can restore application items from restore points created by Veeam Backup & Replication or one of Veeam Agents. For more information on Veeam Agents support in Enterprise Manager, see [Veeam Agents Support](em_support_physical.md).

With Enterprise Manager, you can restore the following application items:

* [Microsoft Exchange items](restore_msexchange.md)
* [Microsoft SQL Server databases](restore_mssql.md)
* [Oracle databases](restore_oracle.md)
* [PostgreSQL instances](restore_postgresql.md)

Before You Begin

Before you restore application items, consider the following:

* Application item restore is available in the Enterprise and Enterprise Plus editions of Veeam Backup & Replication.
* Enterprise Manager does not support application item restore from storage snapshots.
* Enterprise Manager users can only restore Microsoft Exchange items to the original location within their restore scope. Users must also have sufficient permissions to restore application items. Users with the Portal Administrator role have no limitations. For more information, see [Configuring Accounts and Roles](veeam_backup_em_roles.md).

* For details on supported application versions, see the [Platform Support](https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html?ver=13#supported-applications) section of the Veeam Backup & Replication User Guide.
* You can restore deleted Microsoft Exchange items to the production mailbox only.

* Enterprise Manager does not support application item restore from backups created by Veeam Plug-in for Oracle RMAN.

* When you restore application items with Enterprise Manager, restore limitations listed in the Veeam Explorers User Guide are also applied:

* [Veeam Explorer for Microsoft Exchange](https://helpcenter.veeam.com/docs/vbr/userguide/vex_considerations.html?ver=13#restore)
* [Veeam Explorer for Microsoft SQL Server](https://helpcenter.veeam.com/docs/vbr/userguide/vesql_considerations.html?ver=13#restore)
* [Veeam Explorer for Oracle](https://helpcenter.veeam.com/docs/vbr/userguide/veor_considerations.html?ver=13)
* [Veeam Explorer for PostgreSQL](https://helpcenter.veeam.com/docs/vbr/userguide/vep_considerations.html?ver=13)


