---
title: "Used Ports"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/used_ports.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Used Ports


Veeam Backup & Replication within the Veeam Plug-In for Kasten solution is deployed on a machine that uses the same ports as those listed in the [Ports](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13) section of the Veeam Backup & Replication User Guide. Make sure to check that section and add any required ports to achieve the intended Veeam Backup & Replication and Veeam Kasten integration. In addition, Veeam Plug-In for Kasten also uses ports listed in the following table. For more information on Veeam Kasten network ports, see [this Kasten article](https://kb.kasten.io/knowledge/kasten-k10-network-ports).

|  |
| --- |
| Note |
| During installation, Veeam Backup & Replication automatically creates firewall rules for the required ports to allow communication for the application components. |

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Kasten | Veeam Backup & Replication server | TCP | 10006 | Port used to connect to the Veeam Backup & Replication server. |
| VBR RestAPI Service | HTTPS | 9419 | Port used to validate Veeam Backup & Replication Location Profile. |
| Veeam backup repository | TCP | 6162  2500 to 3300 | Default range of ports used for communication with a backup repository.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Backup server | Backup server | TCP/HTTPS | 6172 | Used by the Kasten Plug-in for Veeam Backup & Replication to enable communication with the Veeam Backup & Replication database. |
| Veeam Kasten | TCP/HTTPS | 443 | Used by the Kasten Plug-in for Veeam Backup & Replication to connect to Kasten. |
| Veeam Backup & Replication Remote Console | Veeam Kasten | TCP | 443 | Needed if you want to open Veeam Kasten instance web UI from Remote Console for restores or dashboard access. |


