---
title: "Backup & Replication Console"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_console.html"
last_updated: "12/22/2025"
product_version: "13.0.1.1071"
---

# Backup & Replication Console

In this article

The Veeam Backup & Replication console is a client-side component that provides access to the backup server. The console allows you to log in to Veeam Backup & Replication and perform all kinds of data protection and disaster recovery operations on the backup server.

To connect to the backup server, the Veeam Backup & Replication console uses Simple and Protected GSS-API Negotiation Mechanism (SPNEGO), the Microsoft Windows built-in authentication mechanism. SPNEGO supports both NTLM and Kerberos authentication.

|  |
| --- |
| Note |
| Using NTLM increases the attack surface of your backup infrastructure. To build a more secure environment, disable NTLM and leave Kerberos the only domain authentication protocol. For more information, see [Kerberos Authentication](kerberos_authentication.md). |

The console does not have a direct access to the backup infrastructure components and configuration database. Such data as user credentials, passwords, roles and permissions are stored on the backup server side. To access the data, the console connects to the backup server and queries this information periodically during the work session.

Data stored in the configuration database is encrypted with specific data protection mechanisms. For more information, see [How Database Data Encryption Works](encryption_database_hiw.md).

To make users work as uninterrupted as possible, the remote console maintains the session for 5 minutes if the connection is lost. If the connection is re-established within this period, you can continue working without re-logging to the console.

Backup & Replication Console Deployment

If your installation is based on Veeam Software Appliance, install the console on any Windows machine and access Veeam Backup & Replication remotely over the network. If your installation is based on a Windows backup server, the console is installed locally on the backup server by default. You can also use it in a standalone mode — install the console on any machine and access Veeam Backup & Replication remotely over the network. To learn how to install the console, see [Installing Veeam Backup & Replication Console](install_console.md).

You can install as many remote consoles as you need so that multiple users can access Veeam Backup & Replication simultaneously. Veeam Backup & Replication prevents concurrent modifications on the backup server. If several users are working with Veeam Backup & Replication at the same time, the user who saves the changes first has the priority. Other users will be prompted to reload the wizard or window to get the most recent information about the changes in the configuration database.

If you have multiple backup servers in the infrastructure, you can connect to any of them from the same console. For convenience, you can save several shortcuts for these connections.

|  |
| --- |
| Important |
| You cannot use the same console to connect to backup servers with different versions of Veeam Backup & Replication. Note this if you have more than one backup server in your backup environment, and these backup servers run different versions of Veeam Backup & Replication. For example, if one of your backup servers run version 11, and another backup server runs version 12.1.2, you will need to use 2 separate consoles for connecting to these servers. |

The console supports automatic update. Every time you connect to the backup server locally or remotely, the console checks for updates. If the backup server has updates installed, the console will be updated automatically.

Consider the following:

* Upgrade the console to Veeam Backup & Replication 13.0.1 (build 13.0.1.180) is supported starting from Veeam Backup & Replication 12.3.2 P1 (build 12.3.2.4165). If your console has this version, you can upgrade it automatically upon connecting to the Veeam backup server 13.0.1 (build 13.0.1.180). Automatic upgrade is not supported for Preview, Beta or RTM versions of Veeam Backup & Replication.
* Downgrade of the console is not supported. If the console is of a higher version than the backup server (for example, you have upgraded the console manually), the connection to the server will fail.

If other Veeam Backup & Replication components, such as Veeam Cloud Connect Portal or Veeam Backup Enterprise Manager, are installed on the machine where the console runs, these components will also be upgraded.

Backup & Replication Console Components

When you install a remote console on a machine, Veeam Backup & Replication installs the following components:

* Veeam Backup PowerShell Module
* Veeam Explorer for Microsoft Active Directory
* Veeam Explorer for Microsoft Exchange
* Veeam Explorer for Microsoft OneDrive for Business
* Veeam Explorer for Microsoft SharePoint
* Veeam Explorer for Microsoft SQL Server
* Veeam Explorer for Microsoft Teams
* Veeam Explorer for Oracle
* Veeam Explorer for PostgreSQL
* Veeam Explorer for SAP HANA
* Veeam Data Mover Service/Veeam Transport Service
* Veeam Explorers Recovery Service
* Veeam Installer Service
* Veeam Mount Service

Backup & Replication Console User Access Rights

To log in to Veeam Backup & Replication using the console, the user must be added to the Local Users group on the backup server or a group of domain users who have access to the backup server. The user can perform the scope of operations permitted by his or her role in Veeam Backup & Replication. For more information, see [Users and Roles](users_roles.md).

Requirements for Backup & Replication Console

A machine on which you install the Veeam Backup & Replication console must meet the following requirements:

* The machine must meet the system requirements. For more information, see [System Requirements](system_requirements.md#console).
* The remote console can be installed on a Microsoft Windows machine (physical or virtual).
* The system time on both the backup server and the console must be synchronized with an external time source, such as a Network Time Protocol (NTP) server.
* If you install the console remotely, you can deploy it behind NAT. However, the backup server must be outside NAT. The opposite type of deployment is not supported: if the backup server is deployed behind NAT and the remote console is deployed outside NAT, you will not be able to connect to the backup server.

Limitations for Backup & Replication Console

The Veeam Backup & Replication console has the following limitations:

* You cannot perform restore from the configuration backup using the remote console.
* The machines on which the remote console is installed are not added to the list of managed servers automatically. For this reason, you cannot perform some operations, for example, import backup files that reside on the remote console machine or assign roles of backup infrastructure components to this machine. To perform these operations, you must add the remote console machine as a managed server to Veeam Backup & Replication. For more information, see [Managing Servers](setup_add_server.md).

Related Topics

* [Installing Veeam Backup & Replication Console](install_console.md)
* [Logging in to Veeam Backup & Replication](logon_to_console.md)

Page updated 12/22/2025

Page content applies to build 13.0.1.1071
