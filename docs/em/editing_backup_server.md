---
title: "Editing Backup Servers"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/editing_backup_server.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Backup Servers


After a backup server was added to the Enterprise Manager infrastructure, you can edit connection settings. After you specify new connection settings, Enterprise Manager will try to connect to the backup server using these settings. If you specify credentials, Veeam Backup Enterprise Manager Service will send them to the backup server for the initial authentication. Otherwise, the Enterprise Manager certificate will be used.

To edit connection settings of a backup server, do the following:

1. Log in to Enterprise Manager using an account with the Portal Administrator role.
2. In the upper-right corner, click Configuration.
3. In the Configuration view, open the Backup Servers section.
4. Select a backup sever from the list and click Edit on the toolbar.

Alternatively, you can right-click the selected backup server and select Edit.

1. Specify new connection settings and click OK.

![Editing Backup Servers](images/backup_server_edit.webp "Configuring Restore Scope")

Page updated 2026-07-16

