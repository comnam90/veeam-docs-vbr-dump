---
title: "cloud_connect_tenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_tenant.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---


In this article

The procedure of tenant accounts registration is performed by the SP on the SP Veeam backup server.

To let a tenant work with Veeam Cloud Connect backup and replication resources, you must register a tenant account on the SP Veeam backup server. Tenants with registered tenant accounts have access to cloud repositories and cloud hosts. Tenants without accounts cannot connect to the SP and use Veeam Cloud Connect resources.

The SP can create tenant accounts of the following types:

* [Standalone tenant account](cloud_connect_user.md) — a regular tenant account. Tenants with account of this type can create backups in a cloud repository and create VM replicas on a cloud host provided to the tenant through a hardware plan.
* [VMware Cloud Director tenant account](cloud_vcd_tenant.md) — a tenant account that provides access to VMware Cloud Director resources of the SP. Tenants with account of this type can create backups in a cloud repository and create VM replicas on a cloud host provided to the tenant through an organization VDC. To learn more about this scenario, see [VMware Cloud Director Support](cloud_vcloud_director.md).

|  |
| --- |
| Note |
| Consider the following:   * When you create a tenant account, remember to save a user name and password for the created account. You must pass this data to your tenant. When adding the SP on the tenant Veeam backup server, the tenant must enter the user name and password for the tenant account registered on the SP side.  * By default, in case the SP backup server is managed by Veeam Service Provider Console version 5.0 or later, you cannot create tenant accounts in Veeam Backup & Replication. You can change this setting in Veeam Service Provider Console. To learn more, see the [Managing Veeam Cloud Connect Servers](https://helpcenter.veeam.com/docs/vac/provider_admin/connect_cloud_server.html?ver=9) section in the Guide for Service Providers. |

Related Tasks

* [Configuring Standalone Tenant Account](cloud_connect_user.md)
* [Configuring VMware Cloud Director Tenant Account](cloud_vcd_tenant.md)
* [Managing Tenant Accounts](cloud_connect_manage.md)

Page updated 10/30/2025

Page content applies to build 13.0.1.1071
