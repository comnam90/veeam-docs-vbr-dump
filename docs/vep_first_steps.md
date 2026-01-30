---
title: "Launching Application and Exploring Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_first_steps.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Launching Application and Exploring Backups


To open Veeam Explorer for PostgreSQL, you can use either of the following methods:

* Use the Restore application item option to load PostgreSQL data from a restore point created by Veeam Backup & Replication.

For more information, see [Application Item Restore](restore_veeam_explorers.md).

* Use the Start menu method to, for example, manage ongoing data recovery sessions or check the installed version of Veeam Explorer for PostgreSQL. Note that this method does not load any PostgreSQL data and does not allow you to start new data recovery sessions.

To launch the application, go to Start, click Veeam Explorer for PostgreSQL and perform the following steps:

1. At the Specify Backup Server step, type the DNS name or IP address of the backup server you want to use or select it from the list of recent connections. To save the connection shortcut to the desktop, click Save shortcut in the bottom-right corner.

Click Connect.

[![Specify Backup Server](images/vep_launching_explorer_specify_backup_server.webp)](images/vep_launching_explorer_specify_backup_server.webp "Specify Backup Server")

1. When you are connecting to the backup server for the first time, Veeam Explorer for PostgreSQL will ask you to validate the backup server certificate fingerprint. Click View Certificate to see more details about the imported certificate.

Click Yes to install the certificate on the machine where you are launching Veeam Explorer for PostgreSQL.

[![Validate Server Certificate Fingerprint](images/vepg_launching_explorer_certificate.webp)](images/vepg_launching_explorer_certificate.webp "Validate Server Certificate Fingerprint")

1. At the Sign in step, enter the credentials of the user account that you want to use to connect to the backup server. For more information on the required permissions for the user, see [Permissions](vep_permissions.md).

Select the Remember me check box if you do not want to enter the credentials again the next time you sign in to this backup server.

Click Sign in.

Alternatively, select Sign in as current user to use the credentials of the Windows user account currently signed in on the machine where you are launching Veeam Explorer for PostgreSQL.

[![Specify Credentials](images/vep_launching_explorer_specify_credentials.webp)](images/vep_launching_explorer_specify_credentials.webp "Specify Credentials")

In This Section

* [Getting to Know User Interface](vep_know_ui.md)
* [How Mounting Works](vep_mount.md)
* [Viewing Instance Information](vep_view_db_info.md)


