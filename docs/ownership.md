---
title: "Veeam Plug-In Ownership"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ownership.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Veeam Plug-In Ownership

In this article

To manage Veeam Plug-Ins on target computers, you must make Veeam Backup & Replication the owner of these Veeam Plug-Ins. To do this, perform one of the following operations from Veeam Backup & Replication console:

* Using protection group, deploy Veeam Plug-Ins remotely.
* Add computers with standalone Veeam Plug-Ins to a protection group that is configured to deploy Veeam Plug-Ins.

If you add a computer with standalone Veeam Plug-In to a protection group that does not deploy Veeam Plug-Ins, Veeam Backup & Replication will not be the owner of this Veeam Plug-In. In this case, you cannot perform any operations with Veeam Plug-In from the Veeam Backup & Replication console. To learn more, see [Discovery and Deployment Options](protection_group_options.md).

If Veeam Backup & Replication becomes the owner of Veeam Plug-In, this Veeam Plug-In switches to the managed mode. In the managed mode, a limited set of tasks can be done from the computer side.

You can perform the following tasks from the computer side:

* Create the backup using the backup policy configured in the Veeam Backup & Replication console.
* Restore data from backup to the original and new location.

|  |
| --- |
| Important |
| * In case of Veeam Plug-In for Microsoft SQL Server, you can back up a database that is not added to the backup policy on the Veeam Backup & Replication server using the --exclude-from-managed-mode command. In case of other managed Veeam Plug-Ins, you cannot create backup of a database that is not added to the backup policy on the Veeam Backup & Replication server. You can still create backup of such database on other targets. For example, local storage or shared folder. * You cannot edit backup policy settings from the computer side. |

You can run the following commands from the computer side:

| Command | Veeam Plug-In for Oracle RMAN | Veeam Plug-In for SAP HANA | Veeam Plug-In for SAP on Oracle | Veeam Plug-In for Microsoft SQL Server |
| --- | --- | --- | --- | --- |
| --show-config | Yes | Yes | Yes | Yes |
| --help | Yes | Yes | Yes | Yes |
| --set-force-delete | Yes | Yes | Yes | Yes |
| --set-scale-out-cluster-name | No | Yes | No | No |
| --set-backup-for-restore | No | Yes | Yes | No |
| --set-auth-data-for-restore | Yes | Yes | No | Yes |
| --get-backup-id | Yes | No | No | No |
| --set-repository | No | No | No | Yes |
| --exclude-from-managed-mode | No | No | No | Yes |

Checking Veeam Plug-In Ownership

On the computer, you can check the current owner of Veeam Plug-In. If Veeam Plug-In is managed by Veeam Backup & Replication, the following Veeam Backup & Replication connection parameters will be available in the Veeam Plug-In configuration file:

|  |
| --- |
| <VBRConnectionParams vbrHostName=<hostname> vbrPort=<port\_number> vbrUser=<username> vbrDomain=<domain> vbrPassword=<password> vbrName=<name> vbrId=<ID> /> |

where:

* <hostname> — IP address or hostname of the Veeam Backup & Replication server.
* <port\_number> — port over which Veeam Plug-In must communicate with Veeam Backup & Replication. The default port used for communication with the Veeam Backup & Replication server is 10006.
* <username> — a name of the account that has access to the Veeam Backup & Replication server.
* <domain> — a name of the domain in which the account that has access to the Veeam Backup & Replication server is registered.
* <password> — password of the account that has access to the Veeam Backup & Replication server.
* <name> — name of the Veeam Backup & Replication server.
* <ID> — ID of the Veeam Backup & Replication server.

|  |
| --- |
| Important |
| A plug-in can be managed by one Veeam Backup & Replication server only. If Veeam Backup & Replication tries to become the owner of Veeam Plug-In that is already managed by another Veeam Backup & Replication, Veeam Backup & Replication will not change the owner and you will get a warning message. |

Resetting Veeam Plug-In Ownership

If you do not want Veeam Backup & Replication to be the owner of Veeam Plug-In, you can reset the Veeam Plug-In ownership to the standalone mode. For example, this may be useful if you want to repair the backup job metadata .VACM file for the backup.

To reset the ownership, on the computer with Veeam Plug-In, you must do one of the following operations:

* In the Veeam Plug-In configuration file (veeam\_config.xml), delete the Certificate node and all parameters inside the node.
* Delete Veeam Plug-In configuration file.

In case of Windows-based servers, you must also delete certificates from the Microsoft Windows certificate store.

Page updated 11/21/2025

Page content applies to build 13.0.1.1071
