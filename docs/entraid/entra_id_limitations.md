---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_limitations.html"
last_updated: "2/17/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


When you plan to deploy and configure Veeam Backup for Microsoft Entra ID, keep in mind the following limitations and considerations.

Backup Infrastructure

* It is not recommended that you delete or disable the default [general-purpose backup proxy](entra_id_architecture.md#server) deployed during Veeam Backup & Replication installation. Otherwise, Veeam Backup for Microsoft Entra ID will not be able to perform tenant backup, log backup and backup copy operations.
* Veeam Backup for Microsoft Entra ID does not support creation of more than one Microsoft Entra ID backup repository on the backup server.
* Veeam Backup for Microsoft Entra ID supports storing backed-up tenant data in Microsoft Entra ID backup repositories running PostgreSQL 14 or higher.
* Veeam Backup for Microsoft Entra ID supports only [PostgreSQL password authentication](https://www.postgresql.org/docs/current/auth-password.html) to connect to remote Microsoft Entra ID backup repositories. For more information, see [Connecting to Remote Microsoft Entra ID Backup Repository](entra_id_remote_repository_environment.md).

Tenant Backup and Restore

* Veeam Backup for Microsoft Entra ID does not support the Government and China regions.
* Veeam Backup for Microsoft Entra ID does not support backup and restore of Microsoft Entra External ID tenants and Azure B2C tenants.
* Each restore operation is limited to 1000 items per session.
* For one Microsoft Entra ID tenant, you can create only one tenant backup job. One tenant backup job can protect only one tenant.
* Veeam Backup for Microsoft Entra ID does not support restore of the following item types: built-in role, distribution security group, mail-enabled security group.
* By default, Veeam Backup for Microsoft Entra ID does not back up relationships between protected resources and management groups. If you want to add these relationships into the backup scope, you must perform additional configuration steps described in [this Veeam KB article.](https://www.veeam.com/kb4683)
* During one restore session, you can restore items of one type only. For example, only users or only groups, not users and groups.
* [Entire restore of permanently deleted and linked applications and service principles] You can restore a service principle that represents an application only together with this application and within one restore session. If you restore the application in a separate restore session, the restored application gets a new AppID. The service principal will not recognize this new ID, and the restore of the service principal will fail.
* Restore of users synchronized with Microsoft Active Directory (hybrid identities) is possible using Veeam Backup for Microsoft Entra ID. For more information, see [Appendix. Restoring Synchronized Users (Hybrid Identity)](entra_id_restore_sync_users.md).
* Veeam Backup for Microsoft Entra ID does not support restore of Intune Device Configuration of type editionUpgradeConfiguration with application permissions. You can restore this intune policy using delegated permissions only. During restore of Intune Device Configuration of type editionUpgradeConfiguration, the properties License and ProductKey are restored to predefined placeholder values. After restore, these properties must be manually updated in the [Intune Admin Center](https://intune.microsoft.com/).

Log Backup and Restore

* Veeam Backup for Microsoft Entra ID does not support log backup to multi-bucket repositories. For more information, see [Veeam Backup & Replication User Guide](https://helpcenter.veeam.com/docs/vbr/userguide/object_storage_repository.html?ver=13#childbuckets).
* You cannot back up sign-in logs with Microsoft Entra ID free license. With this license, you can back up only audit logs.
* To create a log backup, you must have the backup of the tenant whose logs you want to protect. The latest restore point of this backup must be created within 30 days before the log backup.


