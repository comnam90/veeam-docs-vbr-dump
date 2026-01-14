---
title: "Ports"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vead_ports.html"
last_updated: "1/5/2026"
product_version: "13.0.1.1071"
---

# Ports

In this article

The following table lists network ports that must be opened to manage traffic during recovery of Microsoft Active Directory data.

For information on the ports that must be opened during backup, see [Ports](used_ports.md#guest_processing_components).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Microsoft Active Directory machine | TCP | 445 | Manages communication between the console and Microsoft Directory Services on the domain controller. |
| TCP, UDP | 389 | Ports used for LDAP connections. |
| TCP | 3268 |
| TCP | 636 | Port used for LDAPS (LDAP over SSL/TLS) connections. |
| Backup repository | TCP | 6162 or 2500 to 3300 | Ports used for managing data transfer during restore to the original (remote) machine or another Microsoft Active Directory machine.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |

Page updated 1/5/2026

Page content applies to build 13.0.1.1071
