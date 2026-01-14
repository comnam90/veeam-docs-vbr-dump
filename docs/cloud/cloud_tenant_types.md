---
title: "cloud_tenant_types"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_tenant_types.html"
last_updated: "12/1/2025"
product_version: "13.0.1.1071"
---


In this article

To work with the cloud resources provided by the SP, the tenant uses a tenant account. Veeam Backup & Replication offers the following types of tenant accounts:

* Standalone tenant account — a regular tenant account for Veeam Cloud Connect Backup and Veeam Cloud Connect Replication scenarios. When the SP creates an account of this type, the SP specifies a name and password for the account, assigns a quota on the cloud repository to the tenant and subscribes the tenant to a hardware plan. To learn more, see [Veeam Cloud Connect Backup](cloud_backup.md) and [Veeam Cloud Connect Replication](cloud_replication.md).
* VMware Cloud Director tenant account — a tenant account used to provide Veeam Cloud Connect backup and replication resources to VMware Cloud Director organizations. When the SP creates an account of this type, the SP specifies an organization, assigns a quota on the cloud repository to the tenant and specifies an organization VDC that will be used as a cloud host for tenant VM replicas. To learn more, see [VMware Cloud Director Tenant Account](cloud_vcloud_director_tenant.md).

|  |
| --- |
| Note |
| Starting from Veeam Backup & Replication version 13, SP can no longer create new Active Directory tenant accounts in Veeam Cloud Connect. However, if the SP has previously configured Active Directory tenant accounts, tenants using supported versions of Veeam Agent or Veeam Backup & Replication (version 12 or earlier) may continue to access the cloud repository with these accounts. The SP can still manage existing Active Directory tenant accounts, but creation of new ones is no longer possible. |

Related Topics

[Tenant Account Credentials](cloud_tenant_creds.md)

Related Tasks

* [Creating Tenant Accounts](cloud_connect_tenant.md)
* [Managing Tenant Accounts](cloud_connect_manage.md)

Page updated 12/1/2025

Page content applies to build 13.0.1.1071
