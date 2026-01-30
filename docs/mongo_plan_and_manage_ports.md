---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_plan_and_manage_ports.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Ports


The following tables describe network ports that must be opened to ensure proper communication of infrastructure components required for MongoDB Backup.

Communication Between Veeam Backup & Replication Components

For details on general requirements for ports that must be opened to ensure proper communication of the backup server with backup infrastructure components, see the [Ports](used_ports.md) for Veeam Backup & Replication.

In addition to general port requirements applicable to a backup server, the following network ports must be opened to enable proper communication between Veeam Backup & Replication components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup Server | Computer with MongoDB | TCP | 22, | Port 22 is used to establish an SSH connection from the Veeam Backup Server to the computer with MongoDB.  Ports 6160 and 6162 are used for default connection to the computer with MongoDB using Veeam Deployer Service and Veeam Transport Service.  Note: You can customize ports 6160 and 6162 using registry keys. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). |
| TCP | 6162 | Default port used by the Veeam Data Mover.  Note: You can customize port 6162 using registry keys. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). |
| TCP | 2500 to 3300 | Default range of ports used for communication between Veeam components during data transmission. For every TCP connection that a backup job uses, one port from this range is assigned. |
| Distribution Server | TCP UDP | 135,  137 to 139,  445, 6160, 11731 | Ports on a Microsoft Windows server used for deploying the Distribution Server component.  Port 135 is optional. This port is used to provide faster Veeam components deployment.  Ports 137 to 139 are used by backup infrastructure components to communicate using NetBIOS if you use NetBIOS in your infrastructure.  Ports 6160 and 11731 are used by the Veeam Installer Service. These ports together with port 445 are mandatory to deploy the Distribution Server component.  Note: You can customize port 6160 using registry keys. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). |
| TCP | 49152 to 65535 | Dynamic RPC port range. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us). |
| TCP | 9380 | Default port used for communication with the Veeam Distribution Service. |
| Distribution Server | Computer with MongoDB | TCP | 22, 6160,  6162 | Port 22 is used to establish an SSH connection for Veeam components transmission and deployment control.  After Veeam components are deployed, ports 6160 and 6162 are used for default connection to the computer with MongoDB using Veeam Deployer Service and Veeam Transport Service.  Note: You can customize ports 6160 and 6162 using registry keys. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). |
| Computer with MongoDB | Veeam Backup Server | TCP | 10002, 10006 | Default ports used for communication with the Veeam Backup server.  Data between the computer with MongoDB and backup repositories is transferred directly, bypassing Veeam backup servers. |
| TCP | 6160,  6162 | Default ports used by Veeam Deployer Service (6160) and Veeam Transport Service (6162) for communication between the computer with MongoDB and Veeam backup server.  Note: You can change the default ports 6160 and 6162 in the respective services' configuration files. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). |

Communication with MongoDB Replica Set

The following table describes network ports that must be opened to ensure proper communication between Veeam backup server and MongoDB replica set that you plan to protect.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication server | MongoDB replica set | TCP | 27017 | Default port used for communication between Veeam Backup & Replication and MongoDB.  You can customize the default port 27017 during [the protection group configuration](mongo_protection_group_scope_deployments.md). |
| Node in a MongoDB replica set | TCP | 27017 | Port for communication between Veeam Backup & Replication and default mongodb configuration.  If you configured a custom port on the mongod side, Veeam Backup & Replication will obtain the port number during [the rescan job](mongo_rescan_job.md). |

Communication with Veeam Backup Repositories

The following table describes network ports that must be opened to ensure proper communication between protected computers and Veeam backup repositories.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Computer with MongoDB | Linux server performing the role of a backup repository | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Microsoft Windows server performing the role of a backup repository | TCP | 49152 to 65535 (for Microsoft Windows 2008 and newer) | Dynamic RPC port range. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us). |
| TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| SMB (CIFS) share performing the role of a backup repository | TCP UDP | 137 to 139,  445 | Ports used as a transmission channel from the Veeam Agent computer to the target SMB (CIFS) share.  Ports 137 to 139 are used by backup infrastructure components to communicate using NetBIOS if you use NetBIOS in your infrastructure. |
| Gateway Microsoft Windows server | TCP UDP | 137 to 139,  445 | If an SMB (CIFS) share is used as a backup repository and a Microsoft Windows server is selected as a gateway server for this CIFS share, these ports must be opened on the gateway Microsoft Windows server.  Ports 137 to 139 are used by backup infrastructure components to communicate using NetBIOS if you use NetBIOS in your infrastructure. |
| TCP | 49152 to 65535 | Dynamic RPC port range. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us). |
| TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |

Communication with 3rd Party Components

The following table describes network ports that must be opened to ensure proper communication between Veeam backup server and 3rd party infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam backup server | Microsoft Active Directory | TCP UDP | 389 | LDAP connections. |
| TCP | 636 | LDAP connections. |
| DNS server with forward/reverse name resolution of all backup servers | UDP | 53 | Port used for communication with the DNS Server. |


