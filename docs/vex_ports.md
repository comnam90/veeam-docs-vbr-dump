---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vex_ports.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Ports


The following table lists network ports that must be opened for managing traffic during recovery of Microsoft Exchange data.

For more information on the ports used during backup, see the following sections:

* [Ports](used_ports.md#guest_processing_components) — for backups created with Veeam Backup & Replication
* [Ports](https://helpcenter.veeam.com/docs/vbo365/guide/vbo_used_ports.html?ver=8) section of the Veeam Backup for Microsoft 365 User Guide — for backups created with Veeam Backup for Microsoft 365.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Target Microsoft Exchange CAS server | TCP | 443, 80 | Port used to connect to the target Microsoft Exchange server. |
| Microsoft Active Directory machine | TCP, UDP | 389 | Ports used for LDAP connections. |
| TCP | 3268 |
| TCP | 636 | Port for LDAPS (LDAP over SSL/TLS) connections. |
| Mail server | TCP | 25, 587 or another port, 443 | Ports used for sending Microsoft Exchange items.  Port 25 is used by default, but you can specify another port in the settings. To use SSL data encryption, specify port 587.  Port 443 is also used and cannot be changed. |
| Backup repository | TCP | 6162 or 2500 to 3300 | Ports used to manage the mounting process.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |


