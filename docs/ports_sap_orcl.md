---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ports_sap_orcl.html"
last_updated: "6/3/2026"
product_version: "13.0.2.29"
---

# Ports


In addition to general port requirements applicable to a backup infrastructure components, the following network ports must be opened to enable proper communication of the SAP on Oracle server and backup infrastructure components.

|  |
| --- |
| Note |
| * For general requirements for ports that must be opened to ensure proper communication of the backup server with backup infrastructure components, see [Ports](used_ports.md) for Veeam Backup & Replication. * The following port requirements apply to Veeam Plug-In for SAP on Oracle operating in the standalone mode. For more information on ports for Veeam Plug-Ins managed by Veeam Backup & Replication, see [Ports for Managed Veeam Plug-Ins](plan_and_manage_used_ports.md). |

Ports

| From | To | Protocol | Port | Notes |
| Database server where Veeam Plug-In is installed | Veeam Backup & Replication server | TCP | 10006,  443 | Default ports used for communication with the Veeam Backup & Replication server.  Note: Data between Veeam Plug-Ins and backup repositories is transferred directly, bypassing the Veeam Backup & Replication server. |
| Backup repository server or [gateway server](gateway_server.md) | TCP | 6162 | Default port used by Veeam Data Mover Service. |


