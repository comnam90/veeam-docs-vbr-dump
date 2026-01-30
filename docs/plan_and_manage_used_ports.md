---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plan_and_manage_used_ports.html"
last_updated: "12/18/2025"
product_version: "13.0.1.1071"
---

# Ports


The following links lead to tables that list network ports that must be opened to ensure proper communication of components in the Veeam Plug-In management infrastructure.

Communication Between Veeam Backup & Replication Components

For details on general requirements for ports that must be opened to ensure proper communication of the backup server with backup infrastructure components, see [Ports](used_ports.md) for Veeam Backup & Replication.

In addition to general port requirements applicable to a Veeam backup server, the backup server used in the Veeam Plug-In management scenario must have the following ports opened:

|  |
| --- |
| Note |
| Veeam Backup & Replication components use Transmission Control Protocol (TCP) for all connections listed in the table below. |

| From | To | Port | Notes |
| --- | --- | --- | --- |
| Veeam backup server | Computer with Veeam Plug-In (Microsoft Windows) | 135, | Ports 135, 137 to 139 and 445 are used to deploy the Veeam Installer Service if you selected in the protection group settings to connect to the computer with Veeam Plug-In using administrator credentials.  Port 6160 is the default port used to connect to the Veeam Installer Service.  Port 6162 is the default port used to connect to the computer with Veeam Plug-In using the Veeam Transport Service.  Port 11731 is the port used to connect to the Veeam Installer Service in Veeam Plug-Ins 12 and earlier versions. If your backup infrastructure contains only Veeam Plug-Ins version 13, you do not need port 11731. |
| Computer with Veeam Plug-In (Linux) | 22, 6160, 6162 | Port 22 is used to establish an SSH connection to the computer with Veeam Plug-In. With this SSH connection, Veeam Backup & Replication transmits Veeam Plug-In installation files and controls the deployment process.  Port 6160 is the default port used to connect to the Veeam Deployer Service.  Port 6162 is the default port used to connect to the computer with Veeam Plug-In using the Veeam Data Mover Service. |
| Distribution server (Microsoft Windows) | 135, 137 to 139, 445, 6160, 6162, 9380, 11731 | Ports 135, 137 to 139, 445 are used to deploy the Veeam Installer Service if you selected in the protection group settings to connect to the computer with Veeam Plug-In using administrator credentials.  Port 6160 is default ports used to connect to the Veeam Installer Service.  Port 6162 is the default port used to connect to the computer with Veeam Plug-In using the Veeam Transport Service.  Port 9380 is the default port used to communicate with the Veeam Distribution Service.  Port 11731 is the port used to connect to the Veeam Installer Service in Veeam Plug-Ins 12 and earlier versions. If your backup infrastructure contains only Veeam Plug-Ins version 13, you do not need port 11731. |
| Distribution server (Linux) | 22, 6160, 6162, 9380 | Port 22 is used to deploy the Distribution Server components.  Ports 6160 is the default port used to connect to the Veeam Installer Service.  Port 6162 is the default port used to connect to the computer with Veeam Plug-In using the Veeam Transport Service.  Port 9380 is the default port used to communicate with the Veeam Distribution Service. |
| Distribution server | Veeam backup server | 443 | Port 443 is used to connect to the Veeam Identity Service. |
| Computer with Veeam Plug-In | 6160 | Port 6160 is used to deploy Veeam Plug-In components. |
| Computer with Veeam Plug-In | Veeam backup server | 10006 | Port 10006 is the default port used by Veeam Plug-In operating in the managed mode to communicate with Veeam backup server.  Keep in mind that backup data is not transferred using port 10006. Backup data between the computer with Veeam Plug-In and backup repositories is transferred directly, bypassing Veeam backup server. |

Communication Between Veeam Plug-In and Veeam Backup & Replication Infrastructure Components

The following sections describe network ports that must be opened to enable proper communication and data transfer between Veeam Plug-In and Veeam Backup & Replication infrastructure components:

* [Veeam Plug-In for Oracle RMAN](ports_vprman.md)
* [Veeam Plug-In for SAP HANA](ports_vpsh.md)
* [Veeam Plug-In for SAP on Oracle](ports_sap_orcl.md)
* [Veeam Plug-In for Microsoft SQL Server](ports_mssql.md)


