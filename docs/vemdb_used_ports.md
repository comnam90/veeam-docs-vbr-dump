---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_used_ports.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Ports

In this article

The following table lists network ports that must be opened for managing traffic during recovery of MongoDB data. For more information on the ports used during backup, see [Ports](mongo_plan_and_manage_ports.md).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Backup server, Veeam Backup & Replication console | Mount server | TCP | 6170 | Port used to communicate with Veeam Mount Service. |
| Mount server | Target Linux machine with MongoDB | TCP | 22 | Default SSH port used as a control channel. This port is also used to deploy and communicate with Veeam Agent for MongoDB. |
| TCP | 27017 | Default port used for connecting to the MongoDB instance. |
| TCP | 2500 to 3300 | Default range of ports used for managing data transfer during restore to the original (remote) machine or another Linux machine with MongoDB. |
| Target Linux machine with MongoDB | Backup repository | TCP | 6162 or 2500 to 3300 | Ports used for managing data transfer during restore to the original (remote) machine or another Linux machine with MongoDB.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |

Page updated 1/15/2026

Page content applies to build 13.0.1.1071
