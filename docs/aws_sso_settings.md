---
title: "Configuring SSO Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_sso_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring SSO Settings


Backup appliances support single sign-on (SSO) authentication based on the SAML 2.0 protocol. SSO authentication scheme allows a user to log in to different software systems with the same credentials using the identity provider service.

To configure SSO settings for the backup appliance, do the following:

1. Switch to the Configuration page.

1. Navigate to General > Identity Provider.

1. In the Identity Provider Configuration section, import identity provider settings from a file obtained from your identity provider:

1. Click Upload Metadata.
2. In the Upload Identity Provider Configuration window, click Browse to locate the file with the identity provider settings.
3. Click Upload.

1. Forward the service provider authentication settings to the identity provider — to obtain the settings, in the Veeam Backup for AWS Configuration section, click Download. The backup appliance will download a metadata file with the service provider authentication settings to your local machine.

Alternatively, you can copy the service provider settings manually:

1. Click Copy Link in the SP Entity ID / Issuer field.
2. Click Copy Link in the Assertion Consumer URL field.

1. [Optional] If you want to sign and encrypt authentication requests sent from the backup appliance to the identity provider, select a certificate with a private key that will be used to sign and encrypt the requests:

1. In the Veeam Backup for AWS Configuration section, click Select in the Certificate field.
2. In the Upload Veeam Backup certificate window, click Browse to locate the certificate file. In the Password field, specify a password used to open the file.
3. Click Upload.

|  |
| --- |
| Note |
| Backup appliances support certificates only in the .PFX and .P12 formats. |

After you configure SSO settings, you can add user accounts that will be able to log in to the backup appliance using single sign-on. For more information, see [Adding User Accounts](aws_accounts_vba_users_create.md).

|  |
| --- |
| Important |
| To authenticate a user whose identity has been received from the identity provider, the backup appliance redirects the user to the identity provider portal. After the user logs in to the portal, the identity provider sends a SAML authentication response to the backup appliance. The SAML response must contain the UserName attribute to allow the backup appliance to identify the user. The attribute value must match the user name that you specify [when creating the user account](aws_accounts_vba_users_create.md).  If your identity provider does not send the UserName attribute by default, you must create a claim rule on the identity provider side to send this attribute in the SAML authentication response to the backup appliance request. |

[![Configuring SSO Settings](images/aws_sso_settings.webp)](images/aws_sso_settings.webp "Configuring SSO Settings")

Page updated 2026-05-22

