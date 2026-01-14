---
title: "used_ports"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/used_ports.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication within the Veeam Plug-In for Kasten solution is deployed on the machine that uses the same ports as those described in the [Ports](https://helpcenter.veeam.com/docs/backup/vsphere/used_ports.html?ver=120) section in the Veeam Backup & Replication User Guide. In addition, Veeam Plug-In for Kasten also uses ports listed in the table. For more information on Veeam Kasten network ports, see [this Kasten article](https://kb.kasten.io/knowledge/kasten-k10-network-ports).

|  |
| --- |
| Note |
| During installation, Veeam Backup & Replication automatically creates firewall rules for the required ports to allow communication for the application components. |

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Kasten | Veeam Backup & Replication server | TCP | 10006 | Port used to connect to the Veeam Backup & Replication server. |
| VBR RestAPI Service | HTTPS | 9419 | Port used to validate Veeam Backup & Replication Location Profile. |
| Veeam backup repository | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Veeam Backup & Replication console and Veeam Backup & Replication and Veeam One server | Veeam Kasten Plug-in for Veeam Backup & Replication | TCP | 9404 | Port used by Veeam Backup & Replication to connect to Kasten Plug-in for Veeam Backup & Replication. |
| Backup server | Backup server | TCP/HTTPS | 6172 | Used by the Kasten Plug-in for Veeam Backup & Replication to enable communication with the Veeam Backup & Replication database. |
| Veeam Kasten | TCP/HTTPS | 443 | Used by the Kasten Plug-in for Veeam Backup & Replication to connect to Kasten. |
| FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during the file-level restore. |

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
