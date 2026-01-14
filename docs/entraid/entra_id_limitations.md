---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_limitations.html"
last_updated: "12/24/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

When you plan to deploy and configure Veeam Backup for Microsoft Entra ID, keep in mind the following limitations and considerations.

Infrastructure

* Veeam Backup for Microsoft Entra ID can use only the default general-purpose backup proxy. This proxy is deployed during Veeam Backup & Replication installation. If you delete or disable this proxy, Microsoft Entra ID tenant backup, log backup and backup copy functionalities will not be available. For more information on the architecture, see [Solution Architecture](entra_id_architecture.md).
* One backup server can work only with one Microsoft Entra ID backup repository. For more information on the architecture, see [Solution Architecture](entra_id_architecture.md).
* Veeam Backup for Microsoft Entra ID supports repositories running on PostgreSQL 14 and higher.
* If you plan to store backed-up data in remote Microsoft Entra ID backup repositories, consider that only PostgreSQL password authentication is supported to connect to these repositories. For more information, see Connecting to Remote Microsoft Entra ID Backup Repository.

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

Page updated 12/24/2025

Page content applies to build 13.0.1.1071
