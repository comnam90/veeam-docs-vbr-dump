---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veo_permissions.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Permissions

In this article

The following table lists the user account permissions necessary to launch Veeam Explorer for Oracle and recover Oracle data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for Oracle launch | The account used to run Veeam Explorer for Oracle must meet the following requirements:   * The account must be a member of the local Administrators or Users group on the machine where Veeam Explorer for Oracle is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for Oracle restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore, Publishing, Instant Recovery, Accessing staging server | When restoring to a Windows machine, make sure to configure user accounts as follows:   * The account must be a member of the local Administrators group on the target machine. In addition, if ASM is used, the account must be a member of the ORA\_ASMADMIN group (for Oracle 12 and higher). * The user account must be granted appropriate permissions to access Oracle databases; Read and Write are the required minimum, Full Control is recommended. * To recover data and copy archived logs to the specified server, the user account must be granted sufficient permissions to access the administrative share.   When restoring to a Linux machine, make sure that the user account has root permissions on the target machine and has membership in the following groups: OSASM [if ASM is used] (typically asmadmin), OSDBA (typically dba), Oracle Inventory group (typically oinstall). |
| Restore from RMAN plug-in backups | When restoring to a Windows machine, make sure to configure user accounts as follows:   * The account must be a member of the local Administrators group and have sysdba privileges. In addition, if ASM is used, the account must be a member of the ORA\_ASMADMIN group (for Oracle 12 and higher). * The account must be granted appropriate permissions to access Oracle databases; Read and Write are the required minimum, Full Control is recommended.  * To restore data to the specified server, the user account must be granted sufficient permissions to access the administrative share.   When restoring to a Linux machine, make sure to configure user accounts as follows:   * The account must be a member of the dba group. In addition, if ASM is used, the account must be a member of the OSASM group (typically asmadmin).  * The account does not need root privileges, but make sure that the following requirements are met:  * If Oracle home on the target machine uses an encrypted wallet, the TNS\_ADMIN (if it is used for the target Oracle home) and ORACLE\_BASE environment variables on the target server must be set. * The resource limits of the user account must be within the recommended range. For more information on user resource limits, see the [Oracle documentation](https://docs.oracle.com/en/database/oracle/oracle-database/21/ladbi/checking-resource-limits-for-oracle-software-installation-users.html#GUID-293874BD-8069-470F-BEBF-A77C06618D5A). |
| Export as database files | The account under which Veeam Explorer for Oracle runs must be a member of the local Administrators group. |

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
