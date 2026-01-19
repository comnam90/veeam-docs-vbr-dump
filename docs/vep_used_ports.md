---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_used_ports.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Ports


The following table lists network ports that must be opened for managing traffic during recovery of PostgreSQL data.

For more information on the ports used during backup, see the Guest Processing Components and Log Shipping Components subsections of the [Ports](used_ports.md) section.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Target Linux machine with PostgreSQL, staging server, mount server | Backup repository | TCP | 6162 or 2500 to 3300 | Default range of ports used for managing data transfer during restore, publish or instant recovery to the original (remote) machine or another Linux machine with PostgreSQL.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |
| Mount Server | Target Linux machine for data export, target Linux machine with PostgreSQL, staging server | TCP | 22, 2500 to 3300 | Port 22 is the default SSH port used as a control channel.  The 2500 to 3300 port range is the default port range for data transfer over the network. |
| Veeam Backup & Replication console (when used as target for data export) | TCP | 6160, 6162 | Ports used when exporting to the Veeam Backup & Replication console (available for Windows-based backup servers only).  Port 6160 is used to connect to the Veeam Installer Service.  Port 6162 is used to connect to the Veeam Data Mover Service. |
| Veeam Backup & Replication console (when used as target for data export) | Staging server, target machine for data publishing | TCP | 2500 to 3300 | Default range of ports used for managing data transfer when exporting to the Veeam Backup & Replication console (available for Windows-based backup servers only). |


