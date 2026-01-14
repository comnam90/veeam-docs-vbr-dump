---
title: "Launching Application and Exploring Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veod_launching.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Launching Application and Exploring Backups

In this article

To open Veeam Explorer for Microsoft OneDrive for Business and load backups, you must manually open Microsoft OneDrive databases. For more information, see [Standalone Databases and External Servers](veod_standalone_databases.md).

To launch the application, go to Start, click Veeam Explorer for Microsoft OneDrive for Business and perform the following steps:

1. At the Specify Backup Server step, type the DNS name or IP address of the backup server you want to use or select it from the list of recent connections. To save the connection shortcut to the desktop, click Save shortcut in the bottom-right corner.

Click Connect.

[![Specify Backup Server](images/veod_launching_explorer_specify_backup_server.webp)](images/veod_launching_explorer_specify_backup_server.webp "Specify Backup Server")

1. When you are connecting to the backup server for the first time, Veeam Explorer for Microsoft OneDrive for Business will ask you to validate the backup server certificate fingerprint. Click View Certificate to see more details about the imported certificate.

Click Yes to install the certificate on the machine where you are launching Veeam Explorer for Microsoft OneDrive for Business.

[![Validate Server Certificate Fingerprint](images/veod_launching_explorer_certificate.webp)](images/veod_launching_explorer_certificate.webp "Validate Server Certificate Fingerprint")

1. At the Sign in step, enter the credentials of the user account that you want to use to connect to the backup server.

Select the Remember me check box if you do not want to enter the credentials again the next time you sign in to this backup server.

Click Sign in.

Alternatively, select Sign in as current user to use the credentials of the Windows user account currently signed in on the machine where you are launching Veeam Explorer for Microsoft OneDrive for Business.

[![Specify Credentials](images/veod_launching_explorer_specify_credentials.webp)](images/veod_launching_explorer_specify_credentials.webp "Specify Credentials")

Consider the following:

* To perform restore operations, Veeam Explorer for Microsoft OneDrive for Business must be run with elevated permissions. The user account must be a member of the local Administrators group on the machine where Veeam Explorer for Microsoft OneDrive for Business is installed.
* The account must have one of the following roles on the backup server:

* The Veeam Backup Administrator or Veeam Restore Operator default roles.
* A custom role with at least the Manage restores permission and the Veeam Explorer for Microsoft OneDrive for Business restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles).

In This Section

* [Getting to Know User Interface](veod_know_ui.md)
* [Browsing, Searching and Viewing Items](veod_browsing_and_searching.md)

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
