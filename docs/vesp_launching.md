---
title: "Launching Application and Exploring Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_launching.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Launching Application and Exploring Backups


To open Veeam Explorer for Microsoft SharePoint and load SharePoint data, you can use either of the following methods:

* Use the Restore application item option to load SharePoint data from a restore point created by Veeam Backup & Replication.

For more information, see [Application Item Restore](restore_veeam_explorers.md).

* Use the Start menu method to manually open Microsoft SharePoint databases. For more information, see [Standalone Databases and External Servers](vesp_standalone_databases.md).

To launch the application, go to Start, click Veeam Explorer for Microsoft SharePoint and perform the following steps:

1. At the Specify Backup Server step, type the DNS name or IP address of the backup server you want to use or select it from the list of recent connections. To save the connection shortcut to the desktop, click Save shortcut in the bottom-right corner.

Click Connect.

[![Specify Backup Server](images/vesp_launching_explorer_specify_backup_server.webp)](images/vesp_launching_explorer_specify_backup_server.webp "Specify Backup Server")

1. When you are connecting to the backup server for the first time, Veeam Explorer for Microsoft SharePoint will ask you to validate the backup server certificate fingerprint. Click View Certificate to see more details about the imported certificate.

Click Yes to install the certificate on the machine where you are launching Veeam Explorer for Microsoft SharePoint.

[![Validate Server Certificate Fingerprint](images/vesp_launching_explorer_certificate.webp)](images/vesp_launching_explorer_certificate.webp "Validate Server Certificate Fingerprint")

1. At the Sign in step, enter the credentials of the user account that you want to use to connect to the backup server. For more information on the required permissions for the user, see [Permissions](vesp_permissions.md).

Select the Remember me check box if you do not want to enter the credentials again the next time you sign in to this backup server.

Click Sign in.

Alternatively, select Sign in as current user to use the credentials of the Windows user account currently signed in on the machine where you are launching Veeam Explorer for Microsoft SharePoint.

[![Specify Credentials](images/vesp_launching_explorer_specify_credentials.webp)](images/vesp_launching_explorer_specify_credentials.webp "Specify Credentials")

In This Section

* [Getting to Know User Interface](vesp_know_ui.md)
* [Browsing, Searching and Viewing Items](vesp_browsing.md)


