---
title: "Accessing Veeam Self-Service Backup Portal"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_portal_access.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---


In this article

Members of VMware Cloud Director organizations can access Veeam Self-Service Backup Portal in the following ways:

* [Access by URL](#url)
* [Access from Cloud Director](#plug-in)

For details on required user access rights, see [Access Control](vcd_portal_permissions.md).

Supported Authentication Types

Veeam Self-Service Backup Portal supports the following types of user authentication:

* Cloud Director local users
* LDAP authentication

Additionally, if users access Veeam Self-Service Backup Portal from the Cloud Director UI, the following authentication methods are also supported:

* SAML
* OpenID Connect (OIDC)

Accessing Veeam Self-Service Backup Portal by URL

To access Veeam Self-Service Backup Portal by URL:

1. Open your web browser and enter the following URL in the address bar:

|  |
| --- |
| https://<EnterpriseManagerServer>/vcloud/<OrgName>/<VCDServer> |

where:

* <EnterpriseManagerServer> is a host name or IP address of the host where the Enterprise Manager server resides.

* <OrgName> is a name of the Cloud Director organization.
* <VCDServer> is a host name or IP address of the host where the Cloud Director server resides.

This URL part is optional. If you do not specify a Cloud Director host here, you may be asked to select the host when you log in to the portal.

For example:

|  |
| --- |
| https://enterprise01.tech.local/vcloud/TechCompanyOrg/172.17.53.16 |

1. From the drop-down list, select a display language.

For more information on display languages, see [Managing Languages](em_lang_manage.md).

1. In the Username and Password fields, specify credentials of a Cloud Director account with proper rights.
2. To save the entered credentials for future access, select the Remember me check box.
3. Click Sign in.
4. From the list of hosts with Cloud Director servers, select the one where your organization has been created.

The list of hosts is displayed if multiple Cloud Director servers are added to the Enterprise Manager infrastructure.

Accessing Veeam Self-Service Backup Portal from VMware Cloud Director

In the VMware Cloud Director environment, Veeam Self-Service Backup Portal is displayed in English by default. When you access the portal by its URL, you can select a preferred language from the drop-down list on the login page. After you select the language here, you can work with the portal in the selected language from the VMware Cloud Director environment. For more information, see [Accessing Veeam Self-Service Backup Portal by URL](#url).

Before members of Cloud Director organizations can access Veeam Self-Service Backup Portal from the Cloud Director UI, the Cloud Director system administrator must upload and configure Veeam Plug-in for VMware Cloud Director. For more information, see [Veeam Plug-in for VMware Cloud Director](vcd_plugin_upload_configure.md).

To access Veeam Self-Service Backup Portal from Cloud Director:

1. Log in to VMware Cloud Director Tenant Portal under a Cloud Director account with proper rights.
2. From the More menu, select Data Protection with Veeam.

If you have a connection error when accessing Veeam Plug-in for VMware Cloud Director, add the Veeam Backup Enterprise Manager certificate as trusted to your browser.

Page updated 10/30/2025

Page content applies to build 13.0.1.1071
