---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_used_ports.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Ports


Veeam Backup & Replication automatically creates firewall rules for the ports required to allow communication between the Proxmox VE server, workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Worker | Proxmox VE server | TCP/HTTPS | 8006 | Used to communicate with the REST API service running on the Proxmox VE server. |
| Proxmox VE server | SSH | 22 | Used to communicate with Proxmox VE server. |
| Backup server | TCP | 10006 | Used to communicate with the backup server. |
| Backup server | TCP | 2500 to 3300 | Default range of ports used for ransomware index transfer. |
| Veeam backup repository or [gateway server](gateway_server.md) | TCP | 2500 to 3300 | Default range of ports used as transmission channels for jobs and restore sessions. For each TCP connection that a job uses, one port from this range is assigned. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Veeam Update Repository  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) | TCP/HTTPS | 443 | Used to download worker deployment packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Worker | TCP | 19000 | Used to communicate with workers. |
| Worker | TCP/HTTPS | 443 | Used by the Platform Service to enable communication with the Veeam Updater service on the worker. |
| Backup server | TCP/HTTPS | 6172 | Used by the Platform Service to enable communication with the Veeam Backup & Replication database. |
| Proxmox VE server | TCP/HTTPS | 8006 | Used to communicate with the REST API service running on the Proxmox VE server. |
| Proxmox VE server | SSH | 22 | Used to communicate with the Proxmox VE server. |
| FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during file-level restore. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see [Ports](used_ports.md). |

Guest Processing Components

The following table describes the network ports that must be opened to ensure proper communication between the backup server and the VMs that will be added to Managed Servers as Guest Interaction Proxy (Log Shipping Server).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Guest interaction proxy | TCP | 445, 135 | Ports used for adding Windows VMs to managed servers using local administrator credentials. Note: Kerberos domain account with administrator privileges should be used. |
| TCP | 6160 | Port used for adding both Windows and Linux VMs to managed servers using a certificate-based authentication. Note: Deployment kit should be pre-installed on VMs. |
| TCP | 22 | Port used for adding Linux VMs to managed servers using SSH credentials. |

Connections with Non-Persistent Runtime Components

The following tables describe network ports that must be opened to ensure proper communication of the backup server and backup infrastructure components with the non-persistent runtime components deployed inside the VM guest OS for application-aware processing and indexing.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Guest interaction proxy | TCP | 6190 | Port used for communication with the guest interaction proxy. |
| Guest interaction proxy | ESXi server | TCP | 443 | Default port used for connections to ESXi host.  [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 is required by vCenter Web Services. |

Network ports described in the following table are NOT required in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | VM guest OS (Microsoft Windows) | TCP | 445, 135 | Port used to deploy the runtime coordination process on the VM guest OS. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |
| TCP | 6173 | Port used by the runtime process deployed inside the VM for guest OS interaction. |
| VM guest OS (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |

Connections with Persistent Agent Components

The following table describes network ports that must be opened to ensure proper communication of the backup server with the persistent agent components deployed inside the VM guest OS for application-aware processing and indexing.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | VM guest OS (Linux) | TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| TCP | 6162 | Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| VM guest OS (Windows) | TCP | 6160, 11731 | Default port and failover port used by Veeam Installer Service. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing and file system indexing. |

Log Shipping Components

The following tables describe network ports that must be opened to ensure proper communication between log shipping components.

* [Log Shipping Server Connections](#log_shipping_server_connections)
* [MS SQL Guest OS Connections](#sql_guest_os_connections)
* [Oracle Guest OS Connections](#oracle_guest_os_connections)
* [PostgreSQL Guest OS Connections](#postgresql_guest_os_connections)

Log Shipping Server Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Log shipping server | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Hyper-V host | Log shipping server (backup server) | TCP | 6162 or 2500 to 3300 | Port or range of ports used for communication with the Hyper-V host and for transfer log backups.  These ports are required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Log shipping server | Backup repository or gateway server | TCP | 6162 or 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Log shipping server (backup server) | Hyper-V host | TCP | 6162 or 2500 to 3300 | Port or range of ports used for communication with the Hyper-V host and for transfer log backups.  These ports are required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Log shipping server | ESXi host | TCP | 443 | Default port used for communication with a log shipping server and transfer log backups over vSphere API. |

MS SQL Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | MS SQL VM guest OS | TCP | 445, 135, 137, 139 | [Non-persistent runtime components only] Ports used for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component.  These ports are not required:   * When working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.   Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing. |
| TCP | 6160, 11731 | [Persistent agent components only] Default port and failover port used by Veeam Installer Service. |
| TCP | 6167 | Port used by the Veeam Log Shipping Service for preparing the database and taking logs. |
| MS SQL VM guest OS | Backup repository | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the MS SQL server has a direct connection to the backup repository. |
| MS SQL VM guest OS | Log shipping server | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a log shipping server and transfer log backups. |

Oracle Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | Oracle VM guest OS (Microsoft Windows) | TCP | 445, 135 | [Non-persistent runtime components only] Ports used for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component.  These ports are not required:   * When working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.   Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing |
| TCP | 6160, 11731 | [Persistent agent components only] Default port and failover port used by Veeam Installer Service. |
| TCP | 6167 | Port used by the Veeam Log Shipping Service for preparing the database and taking logs. |
| Oracle VM guest OS (Linux) | TCP | 22 | [Non-persistent runtime components only] Default SSH port used as a control channel.  This port is NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6162 | [Persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| Oracle VM guest OS | Backup repository | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the Oracle server has a direct connection to the backup repository. |
| Oracle VM guest OS | Log shipping server | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a log shipping server and transfer log backups. |

PostgreSQL Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | PostgreSQL VM guest OS | TCP | 22 | [Non-persistent runtime components only] Default SSH port used as a control channel.  This port is NOT required when working in networkless mode over vSphere Web Services. |
| TCP | 6162 | [Persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  This port is NOT required when working in networkless mode over vSphere Web Services. |
| PostgreSQL VM guest OS | Backup repository | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the PostgreSQL server has a direct connection to the backup repository. |
| PostgreSQL VM guest OS | Log shipping server | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a log shipping server and transfer log backups. |


