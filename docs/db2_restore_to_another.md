---
title: "Restore to Another Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_another.html"
last_updated: "12/17/2024"
product_version: "13.0.1.1071"
---

# Restore to Another Server


You can restore IBM Db2 databases from Veeam Plug-In backups to another server. To restore databases to another server, you must specify an authentication method to access the backup created for the original server and then select the backup from which you want to restore a database.

Consider the following:

* For restore to another server, you can use backups or backup copies of IBM Db2 databases.
* If you perform restore from a backup that was imported to Veeam Backup & Replication, Veeam Plug-In will automatically create the backup job in Veeam Backup & Replication, because the backup job is required for database restore from Veeam Plug-In backups.
* During the restore process, backup operations are not disabled on the IBM Db2 machine.

Veeam Plug-In supports the following authentication methods to access backups:

* Using credentials of the account under which the backup was created. For details, see [Restore to Another Server Using Configured Authentication](db2_restore_to_another_auth.md).
* Using a security certificate. This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication. For details, see [Restore to Another Server Using Credentials](db2_restore_to_another_creds.md).
* Using a recovery token. This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication. To use this option, a backup administrator must create a recovery token for the backup in Veeam Backup & Replication. For details, see [Restore to Another Server Using Recovery Token](db2_restore_to_another_token.md).

You can also perform a redirected restore if you need to restore to a instance with a name that is different from the backed-up instance. For details, see [Restore to Instance with Different Name](db2_restore_to_server_with_different_name.md).


