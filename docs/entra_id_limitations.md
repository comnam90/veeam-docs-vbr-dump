---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entra_id_limitations.html"
last_updated: "4/22/2026"
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

When protecting tenant data, consider the following:

* Veeam Backup for Microsoft Entra ID does not support backup of Microsoft Entra ID [tenants located in China](https://learn.microsoft.com/en-us/azure/china/), [Azure Government tenants](https://learn.microsoft.com/en-us/azure/azure-government/documentation-government-csp-application#obtaining-your-government-tenant), [external tenants](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations) or [Azure Active Directory B2C tenants](https://learn.microsoft.com/en-us/azure/active-directory-b2c/overview).
* You cannot protect multiple tenants by one backup job. Also, you cannot protect the same tenant by multiple backup jobs.
* Veeam Backup for Microsoft Entra ID does not support restore of [Microsoft Entra built-in roles](https://docs.azure.cn/en-us/entra/identity/role-based-access-control/permissions-reference), [distribution security groups](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/new-distributiongroup?view=exchange-ps) or [mail-enabled security groups](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups).
* By default, Veeam Backup for Microsoft Entra ID does not back up relationships between items of protected Microsoft Entra ID tenants and Azure management groups. To back up these relationships, you must perform additional configuration steps described in [this Veeam KB article](https://www.veeam.com/kb4683).
* You cannot restore more than 1000 tenant items during one restore session. Also, you cannot restore multiple item types simultaneously.
* It is recommended that you restore service principals and the applications they represent together, during the same restore session. Otherwise, the applications will be restored with new IDs — as a result, the service principals will fail to be restored.

Log Backup and Restore

When protecting sign-in and audit logs, consider the following:

* Veeam Backup for Microsoft Entra ID does not support storing backed-up sign-in and audit logs in multi-bucket repositories. For more information, see section [Object Storage Repository](object_storage_repository.md).
* Veeam Backup for Microsoft Entra ID does not support backup of sign-in logs with a free Microsoft Entra ID license.
* To create a log backup, you must first back up the tenant whose logs you want to protect; keep in mind that the latest restore point of the tenant backup must be created within 30 days before the log backup.


