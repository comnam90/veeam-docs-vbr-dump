---
title: "Configuring Backup Server Roles"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vbr_server_roles.html"
last_updated: "8/22/2025"
product_version: "13.0.1.1071"
---

# Configuring Backup Server Roles


Veeam Backup Enterprise Manager communicates with backup servers using TLS certificates that you specify when adding the backup servers. For more information, see [Adding Backup Servers](adding_backup_server.md).

All operations on the backup server side are performed by Veeam Backup Service. The service verifies beforehand if Enterprise Manager has rights to accomplish the necessary actions. The account used by Enterprise Manager must have the Veeam Backup Administrator role assigned in Veeam Backup & Replication.

By default, when you install Veeam Backup & Replication on a backup server, the Veeam Backup Administrator role is assigned to the Windows Server Administrators group, so you can choose a user from the Administrators group as an account that will be used to communicate with the backup server. As soon as the group settings can be changed, it is recommended to explicitly assign the Veeam Backup Administrator role to the user account. For more information on assigning roles, see the [Roles and Users](https://helpcenter.veeam.com/docs/vbr/userguide/users_roles.html?ver=13) section of the Veeam Backup & Replication User Guide.


