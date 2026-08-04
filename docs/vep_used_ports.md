---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_used_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Ports


The following table lists network ports that must be opened for managing traffic during recovery of PostgreSQL data.

For more information on the ports used during backup, see the Guest Processing Components and Log Shipping Components subsections of the [Ports](used_ports.md) section.

Ports

| From | To | Protocol | Port | Notes |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Mount server | Target Windows machine with PostgreSQL, Windows-based staging server | TCP | 135, 445 | Ports used to deploy the runtime coordination process on the target machine. |
| TCP | 6173 | Port used by the runtime coordination process that is deployed on the target machine. |
| TCP | 6160 | Port used to communicate with Veeam Installer Service. |
| TCP | 1090 | Port used by the Veeam PostgreSQL Restore Service persistent component installed on a target or staging PostgreSQL machine. |
| Target Windows machine for data export | TCP | 6160, 6162 | Ports used when exporting to Windows machines (available for Windows-based backup servers only).  Port 6160 is used to connect to the Veeam Installer Service.  Port 6162 is used to connect to the Veeam Data Mover Service. |
| Target Linux machine for data export, target Linux machine with PostgreSQL, Linux-based staging server | TCP | 22, 2500 to 3300 | Port 22 is the default SSH port used as a control channel.  The 2500 to 3300 port range is the default port range for data transfer over the network.  For database restore to Linux-based servers, Veeam Explorer for PostgreSQL also requires the port of the target instance. |
| Backup server, target Windows machine with PostgreSQL, Windows-based staging server | Mount server | TCP | 6170 | Port used for communication with Veeam Mount Service. |
| TCP | 3260 to 3270 | Port range opened by Veeam Backup & Replication to manage iSCSI traffic during restore to the target machine.  This port range is opened only during application item restore.  For more information, see [How Mounting Works](vep_mount.md). |
| Target machine with PostgreSQL, staging server, mount server | Backup repository | TCP | 6162 or 2500 to 3300 | Default range of ports used for managing data transfer during restore, publish or instant recovery to the original (remote) machine or another machine with PostgreSQL. Applies for both Windows and Linux PostgreSQL machines.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |
| Target Windows machine for data export | Staging server, target machine for data publishing | TCP | 2500 to 3300 | Default range of ports used for managing data transfer when exporting to Windows machines (available for Windows-based backup servers only). |

Page updated 2026-07-29

