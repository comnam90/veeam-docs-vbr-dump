---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ports_sap_orcl.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Ports


For general requirements for ports that must be opened to ensure proper communication of the backup server with backup infrastructure components, see [Ports](used_ports.md).

In addition to general port requirements applicable to a backup infrastructure components, the following network ports must be opened to enable proper work of Veeam Plug-Ins.

SAP on Oracle Server

The following table describes network ports that must be opened to ensure proper communication of the SAP on Oracle server and backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Database server where Veeam Plug-In is installed | Veeam Backup & Replication server | TCP | 10006, | Default ports used for communication with the Veeam Backup & Replication server.  Note: Data between Veeam Plug-Ins and backup repositories is transferred directly, bypassing the Veeam Backup & Replication server. |
| Backup repository server or [gateway server](gateway_server.md) | TCP | 6162 | Default port used by Veeam Data Mover Service. |

Backup Repositories and Gateway Servers

Depending on the type of backup repositories that you use for Veeam Plug-In backups, the following ports must be open to allow communication between backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Direct Attached Storage | | | | |
| Veeam Backup & Replication server | Backup repository server or [gateway server](gateway_server.md) | TCP | 6162 | Default port used by Veeam Data Mover Service. |
| Microsoft Windows server used as a backup repository or [gateway server](gateway_server.md) | TCP | 6160 | Default port used by the Veeam Installer Service and Veeam Data Mover Service. |
| Network Attached Storage | | | | |
| Gateway server  (specified in the SMB share repository settings) | SMB server | TCP | 445 | Default port used by SMB transport protocol. |
| TCP  UDP | 135, | SMB/NetBIOS name resolution for SMB protocol is needed in some cases. For details, see [Used Ports](used_ports.md). |
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


