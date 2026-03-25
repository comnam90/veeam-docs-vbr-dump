---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entra_id_limitations.html"
last_updated: "3/24/2026"
product_version: "13.0.1.2067"
---

# Considerations and Limitations


When you plan to deploy and configure Veeam Backup for Microsoft Entra ID, keep in mind the following limitations and considerations.

Backup Proxies

When managing [general-purpose backup proxies](backup_proxy_general.md), consider the following:

* During Veeam Backup & Replication installation, a default general-purpose backup proxy is automatically added to the backup infrastructure. Do not remove or disable this proxy — otherwise, you will not be able to protect Microsoft Entra ID tenants and their logs.

Backup Repositories

When connecting a [remote Microsoft Entra ID backup repository](entra_id_remote_repository_environment.md) to the backup infrastructure, consider the following:

* The repository must run PostgreSQL version 14 or later.
* Veeam Backup for Microsoft Entra ID supports connecting one remote Microsoft Entra ID backup repository only.
* Veeam Backup for Microsoft Entra ID supports [PostgreSQL password authentication](https://www.postgresql.org/docs/current/auth-password.html) only.

Tenant Backup and Restore

* Veeam Backup for Microsoft Entra ID does not support backup of Microsoft Entra ID [tenants located in China](https://learn.microsoft.com/en-us/azure/china/), [Azure Government tenants](https://learn.microsoft.com/en-us/azure/azure-government/documentation-government-csp-application#obtaining-your-government-tenant), [external tenants](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations) or [Azure Active Directory B2C tenants](https://learn.microsoft.com/en-us/azure/active-directory-b2c/overview).
* Veeam Backup for Microsoft Entra ID does not support restore of more than 1000 tenant items during one restore session.
* You cannot protect multiple tenants by one backup job — one backup job can be used to protect only one tenant. Also, you cannot protect the same tenant by multiple backup jobs.
* Veeam Backup for Microsoft Entra ID does not support restore of [Microsoft Entra built-in roles](https://docs.azure.cn/en-us/entra/identity/role-based-access-control/permissions-reference), [distribution security groups](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/new-distributiongroup?view=exchange-ps) and [mail-enabled security groups](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups).
* By default, Veeam Backup for Microsoft Entra ID does not back up relationships between protected tenant items and Azure management groups. To instruct Veeam Backup for Microsoft Entra ID to add these relationships to backup jobs, you must perform additional configuration steps described in [this Veeam KB article](https://www.veeam.com/kb4683).
* Veeam Backup for Microsoft Entra ID does not support restoring more than one type of tenant items at a time.
* You can restore a service principal that represents an application only together with this application and within one restore session. If you restore the application and the principal separately, the restored application gets a new ID assigned, and the restore of the service principal will fail.
* Restore of users synchronized with Microsoft Active Directory (hybrid identities) is possible using Veeam Backup for Microsoft Entra ID. For more information, see [Appendix. Restoring Synchronized Users (Hybrid Identity)](entra_id_restore_sync_users.md).
* Veeam Backup for Microsoft Entra ID does not support restore of Intune device configuration profiles of the editionUpgradeConfiguration type with application permissions. You can restore this intune policy using delegated permissions only. During restore of Intune Device Configuration of type editionUpgradeConfiguration, the properties License and ProductKey are restored to predefined placeholder values. After restore, these properties must be manually updated in the [Intune Admin Center](https://intune.microsoft.com/).

Log Backup and Restore

* Veeam Backup for Microsoft Entra ID does not support storing backed-up sign-in and audit logs in multi-bucket repositories. For more information, see section [Object Storage Repository](object_storage_repository.md).
* Veeam Backup for Microsoft Entra ID does not support  backup of sign-in logs with a free Microsoft Entra ID license.
* To create a log backup, you must have the backup of the tenant whose logs you want to protect. The latest restore point of this backup must be created within 30 days before the log backup.


