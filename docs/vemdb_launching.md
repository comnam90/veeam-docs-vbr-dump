---
title: "Launching Application"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_launching.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Launching Application


To open Veeam Explorer for MongoDB, you can use either of the following methods:

* Use the Restore MongoDB items option in Veeam Backup & Replication to load backups created in Veeam Backup & Replication. For more information, see [Required Job Settings](vemdb_job_settings.md).

* Use the Start menu method to, for example, manage ongoing restore sessions or check the installed product version. Note that this method does not load any backups and does not allow you to start new restore sessions.

To launch the application, go to Start, click Veeam Explorer for MongoDB and perform the following steps:

1. At the Specify Backup Server step, type the DNS name or IP address of the backup server you want to use or select it from the list of recent connections. To save the connection shortcut to the desktop, click Save shortcut in the bottom-right corner.

Click Connect.

[![Specify Backup Server](images/vemdb_launching_explorer_specify_backup_server.webp)](images/vemdb_launching_explorer_specify_backup_server.webp "Specify Backup Server")

1. When you are connecting to the backup server for the first time, Veeam Explorer for MongoDB will ask you to validate the backup server certificate fingerprint. Click View Certificate to see more details about the imported certificate.

Click Yes to install the certificate on the machine where you are launching Veeam Explorer for MongoDB.

[![Validate Server Certificate Fingerprint](images/vemdb_launching_explorer_certificate.webp)](images/vemdb_launching_explorer_certificate.webp "Validate Server Certificate Fingerprint")

1. At the Sign in step, enter the credentials of the user account that you want to use to connect to the backup server. For more information on the required permissions for the user, see [Permissions](vemdb_permissions.md).

Select the Remember me check box if you do not want to enter the credentials again the next time you sign in to this backup server.

Click Sign in.

Alternatively, select Sign in as current user to use the credentials of the Windows user account currently signed in on the machine where you are launching Veeam Explorer for MongoDB.

[![Specify Credentials](images/vemdb_launching_explorer_specify_credentials.webp)](images/vemdb_launching_explorer_specify_credentials.webp "Specify Credentials")

In This Section

[Getting to Know User Interface](vemdb_know_ui.md)


