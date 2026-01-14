---
title: "em_managing_tenants"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_managing_tenants.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager offers the following types of vSphere Self-Service Backup Portal tenant accounts: User, Group, External User and External Group.

| Type | Description | How to Sign In | Name Format |
| --- | --- | --- | --- |
| User | AD user | By specifying a user name and password | * Windows-based Enterprise Manager: DOMAIN\Username (domain is optional) * Linux-based Enterprise Manager: Username@DOMAIN (domain is mandatory for AD users) |
| Group | AD group | By specifying a user name and password | * Windows-based Enterprise Manager: DOMAIN\Groupname (domain is optional) * Linux-based Enterprise Manager: Groupname@DOMAIN (domain is mandatory for AD groups) |
| External User | IdP user | By using single sign-on\* | Username@Suffix |
| External Group | IdP group | By using single sign-on\* | Free-form string |

\* For more information on the single sign-on capability, see [SAML Authentication Support](em_saml.md).

|  |
| --- |
| Note |
| You cannot create a vSphere Self-Service Backup Portal tenant account for a local user account. |

Veeam Backup Enterprise Manager administrators can perform the following tasks with the tenant accounts:

* [Add a new tenant account](em_adding_tenant_accounts.md)
* [Edit an already created tenant account](em_editing_tenant_accounts.md)
* [Export a report on the created tenant accounts](em_exporting_tenant_accounts_list.md)
* [Remove a tenant account](em_removing_tenant_accounts.md)

Page updated 10/30/2025

Page content applies to build 13.0.1.1071
