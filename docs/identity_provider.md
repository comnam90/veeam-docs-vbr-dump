---
title: "SAML Authentication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/identity_provider.html"
last_updated: "2/18/2026"
product_version: "13.0.1.1071"
---

# SAML Authentication


Veeam Backup & Replication supports single sign-on authentication based on the SAML 2.0 protocol. Enterprise organizations that use a single sign-on (SSO) service in their IT infrastructure can extend single sign-on capabilities to Veeam Backup & Replication. A user of the organization logged in to the single sign-on service can access Veeam Backup & Replication if their account was added by the Veeam Backup Administrator.

SAML authentication scenario involves the following parties:

* User that logs in to the Veeam Backup & Replication console or Veeam Backup & Replication Web UI.
* Service provider (SP) — an application accessed by the user. In the Veeam backup infrastructure, the service provider is Veeam Backup & Replication.
* Identity provider (IdP) — an external service (hosted on premises or in the public cloud) that facilitates SSO. The IdP keeps user identity data in a user store (or attribute store). Upon requests from the SP, the IdP issues SAML authentication assertions, that is, identifies the user and provides the SP with the required information about the user.

The SP and IdP exchange information in the XML format in accordance with the [SAML V2.0 Standard](https://wiki.oasis-open.org/security/FrontPage#SAML_V2.0_Standard).

|  |
| --- |
| Tip |
| The list of tested SAML solutions includes the following vendor product lines:   * Active Directory Federation Services * Microsoft Entra ID * Okta * Auth0 * Keycloak * Cyberark * Thales * Entrust |

How SAML Authentication Works

Veeam Backup & Replication supports the following scenario for SAML authentication:

1. A Veeam Backup Administrator adds an external user account in the Security tab of the Users and Roles window and assigns a role to this user. For more information, see [Adding External Users](#add_external_user).
2. A user runs the Veeam Backup & Replication console or opens the Veeam Backup & Replication Web UI.
3. On the sign-in page, the user clicks Sign in with SSO.
4. Veeam Backup & Replication redirects a SAML authentication request to the IdP. If the user has not previously logged in with the single sign-on service, the IdP redirects the user to the URL of the single sign-on service.

|  |
| --- |
| Note |
| If the user logs in to the desktop application, they must authenticate in the single sign-on service every time. For the web UI, the user logs in automatically until the authorization cookie expires. |

1. After the user authenticates in the single sign-on service, the IdP issues a SAML assertion and redirects it to Veeam Backup & Replication in the SAML response.
2. The user gains access to Veeam Backup & Replication and can perform operations according to the assigned role.

Configuring SAML Authentication

Depending on your identity provider, SAML authentication configuration could require steps that are not listed in this section. For information on how to configure Microsoft Entra ID, see [Configuring SAML Authentication for Microsoft Entra ID](identity_provider_entra_id.md). If you use an alternative identity provider, consult their documentation.

To configure SAML authentication on the Veeam Backup & Replication side, perform the following steps:

1. Get an XML metadata file from your IdP.
2. From the main menu, select Users and Roles.
3. In the User and Roles window, select the Identity Provider tab.
4. Select the Enable SAML authentication check box.
5. In the Identity provider (IdP) information section, specify the IdP metadata file. To do this, click Browse and select the file.
6. In the Service Provider (SP) information section, do the following:

1. Click Install to specify a valid Veeam Backup & Replication server certificate. Your IdP will use this certificate to validate requests from the Veeam Backup & Replication server. You can select an existing certificate from the certificate store or import a certificate from a file. For more information, see [Backup Server Certificate](backup_server_certificate.md).
2. Click Download to get an XML metadata file for your IdP. Use this file to add the Veeam Backup & Replication server as the service provider in your IdP configuration.

1. Click OK.

![SAML Authentication](images/saml_configure.webp)

Adding External Users

After you configure SAML authentication, you can add external users or groups to Veeam Backup & Replication and assign roles to them. To do this, perform the following steps:

1. From the main menu, select Users and Roles.
2. In the User and Roles window, select the Security tab.
3. Click Add > External user or group.
4. From the Type drop-down list, select User or Group.
5. In the Name field, enter the group name or user name in the UPN format, for example, john.doe@domain.com.
6. From the Role drop-down list, select the role that you want to assign to this user or group.
7. Click OK.

![SAML Authentication](images/saml_add_external_user.webp)


