---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_used_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Ports


Veeam Backup & Replication automatically creates firewall rules for the ports required to allow communication between the Proxmox VE server, workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

Workers

| From | To | Protocol | Port | Notes |
| Worker | Proxmox VE server | TCP/HTTPS | 8006 | Used to communicate with the REST API service running on the Proxmox VE server. |
| Proxmox VE server | SSH | 22 | Used to communicate with Proxmox VE server. |
| Backup server | TCP | 10006 | Used to communicate with the backup server. |
| Backup server | TCP | 2500 to 3300 | Default range of ports used for ransomware index transfer. |
| Veeam backup repository or [gateway server](gateway_server.md) | TCP | 6162 (2500 to 3300) | Default range of ports used as transmission channels for jobs and restore sessions. The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Veeam Update Repository (repository.veeam.com)  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) (cloudfront.net, amazonaws.com) | TCP/HTTPS | 443 | Used to download worker deployment packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |
| NTP server | UDP | 123 | Used for time synchronization with NTP servers. |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

Backup Server

| From | To | Protocol | Port | Notes |
| Backup server | Worker | TCP | 19000 | Used to communicate with workers. |
| Worker | TCP/HTTPS | 443 | Used by the Platform Service to enable communication with the Veeam Updater service on the worker. |
| Backup server | TCP/HTTPS | 6172 | Used by the Platform Service to enable communication with the Veeam Backup & Replication database. |
| Proxmox VE server | TCP/HTTPS | 8006 | Used to communicate with the REST API service running on the Proxmox VE server. |
| Proxmox VE server | SSH | 22 | Used to communicate with the Proxmox VE server. |
| FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during file-level restore. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see [Ports](used_ports.md). |

Page updated 2026-07-08

