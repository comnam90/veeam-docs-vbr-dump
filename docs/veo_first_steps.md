---
title: "Launching Application and Exploring Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veo_first_steps.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Launching Application and Exploring Backups


To open Veeam Explorer for Oracle, you can use any of the following methods:

* Use the Restore application item option to load Oracle data from a restore point created by Veeam Backup & Replication.

For more information, see [Application Item Restore](restore_veeam_explorers.md).

* Use the Restore from Oracle RMAN backup option to load backups created by Veeam Plug-In for Oracle RMAN.

For more information, see [Restore with Veeam Explorer for Oracle](restore_veor.md).

* Use the Start menu method to, for example, manage ongoing instant recovery sessions or check the installed product version. Note that this method does not load any Oracle data and does not allow you to start new data recovery sessions.

To launch the application, go to Start, click Veeam Explorer for Oracle and perform the following steps:

1. At the Specify Backup Server step, type the DNS name or IP address of the backup server you want to use or select it from the list of recent connections. To save the connection shortcut to the desktop, click Save shortcut in the bottom-right corner.

Click Connect.

[![Specify Backup Server](images/veor_launching_explorer_specify_backup_server.webp)](images/veor_launching_explorer_specify_backup_server.webp "Specify Backup Server")

1. When you are connecting to the backup server for the first time, Veeam Explorer for Oracle will ask you to validate the backup server certificate fingerprint. Click View Certificate to see more details about the imported certificate.

Click Yes to install the certificate on the machine where you are launching Veeam Explorer for Oracle.

[![Validate Server Certificate Fingerprint](images/veor_launching_explorer_certificate.webp)](images/veor_launching_explorer_certificate.webp "Validate Server Certificate Fingerprint")

1. At the Sign in step, enter the credentials of the user account that you want to use to connect to the backup server. For more information on the required permissions for the user, see [Permissions](veo_permissions.md).

Select the Remember me check box if you do not want to enter the credentials again the next time you sign in to this backup server.

Click Sign in.

Alternatively, select Sign in as current user to use the credentials of the Windows user account currently signed in on the machine where you are launching Veeam Explorer for Oracle.

[![Specify Credentials](images/veor_launching_explorer_specify_credentials.webp)](images/veor_launching_explorer_specify_credentials.webp "Specify Credentials")

In This Section

* [Getting to Know User Interface](veor_know_ui.md)
* [How Mounting Works](veo_mount.md)
* [Viewing Database Information](veo_view_db_info.md)


