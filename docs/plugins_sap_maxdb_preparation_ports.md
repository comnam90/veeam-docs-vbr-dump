---
title: "Ports"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_preparation_ports.html"
last_updated: "1/2/2026"
product_version: "13.0.1.1071"
---

# Ports

In this article

To enable proper work of Veeam Plug-Ins, make sure that the following ports are open.

SAP MaxDB Server

The following table describes network ports that must be opened to ensure proper communication of the SAP MaxDB server and backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| SAP MaxDB server where Veeam Plug-In is installed | Veeam Backup & Replication server | TCP | 10006, 443 | Default ports used for communication with the Veeam Backup & Replication server.  Note that data between Veeam Plug-Ins and backup repositories is transferred directly, bypassing the Veeam Backup & Replication server. |
| Backup repository server or [gateway server](gateway_server.md) | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a backup process uses, one port from this range is assigned. |

Backup Repositories and Gateway Servers

Depending on the type of backup repositories that you use for Veeam Plug-In backups, the following ports must be open to allow communication between backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication server | Backup repository server or gateway server\* | TCP | 2500 to 3300\*\* | Default range of ports used as data transmission channels. For every TCP connection that a backup process uses, one port from this range is assigned. |
| Direct Attached Storage | | | | |
| Veeam Backup & Replication server | Linux server used as a backup repository or gateway server | TCP | 22 | Port used as a control channel from the Veeam Plug-In server to the target Linux host. |
| Microsoft Windows server used as a backup repository or gateway server | TCP  UDP | 135, | Ports used as a management channel from the Veeam Plug-In server to the Repository/Gateway server. Also, the ports are used to deploy Veeam components. |
| TCP | 6160, 6162 | Default ports used by the Veeam Installer Service and Veeam Data Mover Service |
| Network Attached Storage | | | | |
| Gateway server  (specified in the SMB share repository settings) | SMB server | TCP | 445 | Default port used by the SMB transport protocol. |
| TCP  UDP | 135, 137 to 139 | SMB/Netbios name resolution for the SMB protocol (needed in some cases). For details, see [Used Ports](used_ports.md). |
| Gateway server  (specified in the NFS share repository settings) | NFS server | TCP  UDP | 111, 2049 | Standard NFS ports used as a transmission channel from the gateway server to the target NFS share. |
| Dell Data Domain | | | | |
| Veeam Backup & Replication server or Gateway server | Dell Data Domain | TCP | 111 | Port used to assign a random port for the mountd service used by NFS and DDBOOST. Mountd service port can be statically assigned. |
| TCP | 2049 | Main port used by NFS. To change the port, you can use the nfs set server-port command. Note that the command requires SE mode. |
| TCP | 2052 | Main port used by NFS MOUNTD. To change the port, you can use the nfs set mountd-port command. Note that the command requires SE mode. |
| HPE StoreOnce | | | | |
| Veeam Backup & Replication server  or  Gateway server | HPE StoreOnce | TCP | 9387 | Default command port used for communication with HPE StoreOnce. |
| 9388 | Default data port used for communication with HPE StoreOnce. |
| ExaGrid | | | | |
| Veeam Backup & Replication server | ExaGrid | TCP | 22 | Default command port used for communication with ExaGrid. |
| Quantum DXi | | | | |
| Veeam Backup & Replication server | Quantum DXi | TCP | 22 | Default command port used for communication with Quantum DXi. |
| Fujitsu ETERNUS CS800 | | | | |
| Veeam Backup & Replication server | Fujitsu ETERNUS CS800 | TCP | 22 | Default command port used for communication with Fujitsu ETERNUS CS800. |
| Infinidat InfiniGuard | | | | |
| Veeam Backup & Replication server | Infinidat InfiniGuard | TCP | 22 | Default command port used for communication with Infinidat InfiniGuard. |

\* For NFS share, SMB share repositories, and Dell Data Domain, HPE StoreOnce deduplication storage appliances, Veeam Backup & Replication uses an auxiliary backup infrastructure component — gateway server. For details, see [Gateway Server](gateway_server.md).

For a detailed list of ports used by Veeam Backup & Replication server and backup repositories, see [Used Ports](used_ports.md).

Page updated 1/2/2026

Page content applies to build 13.0.1.1071
