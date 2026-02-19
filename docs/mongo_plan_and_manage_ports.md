---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_plan_and_manage_ports.html"
last_updated: "2/18/2026"
product_version: "13.0.1.1071"
---

# Ports


The following tables describe network ports that must be opened to ensure proper communication of infrastructure components required for MongoDB Backup.

Communication Between Veeam Backup & Replication Components and MongoDB Replica Set

For details on general requirements for ports that must be opened to ensure proper communication of the backup server with backup infrastructure components, see the [Ports](used_ports.md) for Veeam Backup & Replication.

In addition to general port requirements applicable to a backup server, the following network ports must be opened to enable proper communication between Veeam Backup & Replication components and MongoDB replica set that you plan to protect..

Communication Between

| From | To | Protocol | Port | Notes |
| Veeam Backup & Replication server | Computer with MongoDB | TCP | 22, | Port 22 is used to establish an SSH connection from the Veeam Backup Server to the computer with MongoDB.  Ports 6160 and 6162 are used for default connection to the computer with MongoDB using Veeam Deployer Service and Veeam Transport Service.  Port 27017 is the default port for communication between the Veeam Backup & Replication server, the MongoDB replica set and the nodes in this replica set.  Notes:   * You can customize ports 6160 and 6162 using registry keys. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). * You can customize port 27017 during [the protection group configuration](mongo_protection_group_scope_deployments.md). In this case, Veeam Backup & Replication uses a custom port to connect to the replica set. During [rescan](mongo_rescan_job.md), Veeam Backup & Replication collects the ports associated with each node added to the protection group. |
| Distribution Server | TCP UDP | 135,  137 to 139,  445, 6160, 9380 | Ports on a Microsoft Windows server used for deploying the Distribution Server component.  Port 135 is optional. This port is used to provide faster Veeam components deployment.  Ports 137 to 139 are used by backup infrastructure components to communicate using NetBIOS if you use NetBIOS in your infrastructure.  Port 6160 is used by the Veeam Installer Service. These ports together with port 445 are mandatory to deploy the Distribution Server component.  Port 9380 is used for communication with the Veeam Distribution Service.  Note: You can customize port 6160 using registry keys. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). |
| Distribution Server | Computer with MongoDB | TCP | 6160 | After Veeam components are deployed, ports 6160 is used for default connection to the computer with MongoDB using Veeam Deployer Service and Veeam Transport Service.  Note: You can customize port 6160 using registry keys. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). |
| Computer with MongoDB | Veeam Backup & Replication server | TCP | 10006 | Default port used by Veeam Agent for communication with the Veeam Backup server.  Note: Port 10006 is not used to transfer backup data. Data between the computer with MongoDB and backup repositories is transferred directly, bypassing the Veeam Backup & Replication server. |

Communication with Veeam Backup Repositories

The following table describes network ports that must be opened to ensure proper communication between protected computers and Veeam backup repositories.

Communication with Veeam Backup Repositories

| From | To | Protocol | Port | Notes |
| Computer with MongoDB | Linux server performing the role of a backup repository | TCP | 6162 | Default port used by the Veeam Data Mover. |
| Microsoft Windows server performing the role of a backup repository | TCP | 6162 | Default port used by the Veeam Data Mover. |
| Gateway Microsoft Windows server | TCP UDP | 6162 | Default port used by the Veeam Data Mover. |
| Object storage repository | TCP | 443 | Port 443 is used to communicate with the object storage repository. To learn the full list of required ports and endpoints, see general ports for [Object Storage Repository](used_ports.md#osrc). |


