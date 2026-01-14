---
title: "Ports"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veo_used_ports.html"
last_updated: "12/23/2025"
product_version: "13.0.1.1071"
---

# Ports

In this article

The following tables list network ports that must be opened to manage traffic during recovery of Oracle data. The used ports depend on whether you are restoring data from image-level backups created with application-aware processing or backups created with Veeam Plug-In for Oracle RMAN.

Data Recovery from Image-Level Backups

This table lists ports that must be opened during recovery from image-level backups of Oracle data.

For information on the ports that must be opened when creating image-level backups of Oracle machines, see the Guest Processing Components and Log Shipping Components subsections of the [Ports](used_ports.md) section.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Backup server, Veeam Backup & Replication console, mount server associated with the backup repository (only for Instant Recovery or restore from Enterprise Manager) | Target Windows machine with Oracle, staging server | TCP, UDP | 135, 445 | Ports used to deploy the runtime coordination process on the target machine or the staging server. |
| TCP | 49152 to 65535 | Recommended dynamic RPC port range.1 For more information, see [this Microsoft article](https://support.microsoft.com/en-us/kb/832017). |
| TCP | 1035 to 1075 | Default range of ports for the Veeam Oracle Restore Service runtime components installed on the target or staging Oracle server to support restore operations. Each runtime component uses the next available port in the range, and only during application item restore.  Note: You must manually open this port range in Microsoft Windows Firewall. |
| Mount server associated with the backup repository | Target Windows machine with Oracle, staging server | TCP | 6160, 445 | Port 6160 is used to connect to the Veeam Installer Service on the target machine or the staging server.  Port 445 is used to deploy the runtime coordination process on the target machine or the staging server. |
| Veeam Backup & Replication console, mount server associated with the backup repository | Target Linux machine with Oracle | TCP | 22 | Default SSH port used as a control channel. |
| Backup server, Veeam Backup & Replication console, mount server associated with the backup repository | Backup repository | TCP | 6162 or 2500 to 3300 | Default range of ports used for managing data transfer.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |
| Target Windows machine with Oracle, staging server | Mount server associated with the backup repository | TCP | 3260 to 3270 | Range of ports opened by Veeam Backup & Replication to manage iSCSI traffic during restore to the target machine.  This port range is opened only during application item restore. |

1 If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports: during setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the RPC function call failed error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls).

Restore from Plug-in Backups

This table lists ports that must be opened during restore from backups created with Veeam Plug-In for Oracle RMAN.

In addition to the ports in the table below, Veeam Explorer for Oracle relies on ports used by Veeam Plug-In for Oracle RMAN. For more information, see [Ports](ports_vprman.md).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Target Windows machine with Oracle | TCP, UDP | 135, 445 | Ports used to deploy the runtime coordination process on the target machine. |
| TCP | 49152 to 65535 | Recommended dynamic RPC port range.1 For more information, see [this Microsoft article](https://support.microsoft.com/en-us/kb/832017). |
| TCP | 1035 to 1075 | Default range of ports for the Veeam Oracle Restore Service runtime components installed on the target Oracle server to support restore operations. Each runtime component uses the next available port in the range, and only during application item restore.  Note: You must manually open this port range in Microsoft Windows Firewall. |
| Target Linux machine with Oracle | TCP | 22 | Default SSH port used as a control channel. |
| Backup server, Veeam Backup & Replication console, target Linux machine with Oracle | Backup repository | TCP | 6162, 2500 to 3300 | Default range of ports used for managing data transfer.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |

1 If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports: during setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the RPC function call failed error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls).

Page updated 12/23/2025

Page content applies to build 13.0.1.1071
