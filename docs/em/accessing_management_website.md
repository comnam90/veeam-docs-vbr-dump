---
title: "Accessing Enterprise Manager"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/accessing_management_website.html"
last_updated: "12/8/2025"
product_version: "13.0.1.1071"
---


In this article

You can access Veeam Backup Enterprise Manager using Enterprise Manager credentials or single sign-on (SSO).

When you open Enterprise Manager for the first time, you must log in as a user with administrative privileges:

* For Microsoft Windows-based Enterprise Manager, enter credentials of a user account with local administrative rights or the account that was used to install Enterprise Manager.
* For Linux-based Enterprise Manager, log in using the veeamadmin account.

To access the Veeam Backup Enterprise Manager website, follow these steps:

1. Open your browser and enter the Enterprise Manager URL in one of the following formats:

* For Microsoft Windows-based Enterprise Manager:

|  |
| --- |
| https://<hostname>:9443 |

* For Linux-based Enterprise Manager (the port number is optional):

|  |
| --- |
| https://<hostname>:443 |

If you cannot access the website over HTTPS, possible causes may include configuration or connectivity issues. For more information, see [this Veeam KB article](https://www.veeam.com/kb1168).

1. From the language drop-down list, select the desired display language. For details on adding new languages, see [Managing Languages](em_lang_manage.md).
2. Log in to Enterprise Manager:

* To log in with Enterprise Manager credentials:

1. In the Username and Password fields, specify your Enterprise Manager credentials. To log in to a Microsoft Windows-based Enterprise Manager with a domain account, enter the user name in the DOMAIN\Username format. To log in to a Linux-based Enterprise Manager with a domain account, enter the user name in the UPN format.
2. To save the entered credentials for future access, select the Remember me option.
3. Click Sign in.

* To log in with the credentials of the Microsoft Windows account that you are currently signed in on the machine where you are launching Enterprise Manager, click Sign in as current user option.

* To log in with SSO, click Sign in with SSO. Enterprise Manager will redirect you to the login webpage of the single sign-on service. Complete the sign-in procedure on the login page. If the account is already authenticated in the single sign-on service, you will immediately access the Enterprise Manager website.

The Sign in with SSO option is available if SAML authentication is configured for Veeam Backup Enterprise Manager. For more information, see [Configuring SAML Authentication Settings](veeam_backup_em_saml.md).

|  |
| --- |
| Note |
| If you log in under a user account that is not assigned an Enterprise Manager role, you will be automatically redirected to the Veeam Self-Service File Restore Portal. On this portal, you can browse and restore only machines on which your user account has local administrative rights. For more information on configuring Enterprise Manager security roles, see [Configuring Accounts and Roles](veeam_backup_em_roles.md). |

After you finish working with Enterprise Manager, or if you need to switch user accounts, click the user name in the upper-right corner of the main window and then click Sign Out.

Related Topics

* [Exploring Enterprise Manager](em_know_ui.md)
* [Configuring Accounts and Roles](veeam_backup_em_roles.md)

Page updated 12/8/2025

Page content applies to build 13.0.1.1071
