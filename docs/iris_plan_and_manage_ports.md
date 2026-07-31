---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_plan_and_manage_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Ports


The following table describes the network ports that must be opened to ensure proper communication of the infrastructure components used to protect IRIS instances. For the general port requirements of the backup server, see [Ports](used_ports.md) for Veeam Backup & Replication.

Ports

| From | To | Protocol | Port | Notes |
| Veeam Backup & Replication server | ODB server | TCP | 22, 6160, 6162 | Port 22 is used to establish an SSH connection from the backup server to the ODB server for the initial deployment of Veeam components. Ports 6160 and 6162 are used to connect to the ODB server through the Veeam Deployer Service and the Veeam Transport Service. You can customize ports 6160 and 6162 using registry keys. For details, see [this Veeam KB article](https://www.veeam.com/kb4519). |
| Linux-based backup proxy | Veeam backup repository | TCP | 6162 | Default port used by the Veeam Data Mover to transfer backup data from the proxy to the backup repository. |
| ODB server | Veeam backup repository | TCP | 6162 | Default port used by the Veeam Data Mover to transfer data from the backup repository to the ODB server during restore from a backup. |
| Linux-based backup proxy, ODB server | Object storage repository | TCP | 443 | Used to communicate with an object storage repository when backups are stored in object storage.  Veeam Backup & Replication communicates with the storage system only over the Universal Storage API. The ports required for this communication depend on the management interface of the storage system. For the exact list, see the documentation of your storage vendor. |

Page updated 2026-07-28

