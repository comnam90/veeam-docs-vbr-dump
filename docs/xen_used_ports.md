---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_used_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Ports


Veeam Backup & Replication automatically creates firewall rules for the ports required to allow communication between the Citrix XenServer pool, workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

Workers

| From | To | Protocol | Port | Notes |
| Worker | Xen pool | TCP/HTTPS | 443 | Used to communicate with the XAPI management service running on the Xen pool. |
| NBD/TLS | 10809 | Used to communicate with Xen pools when using the NBD transport mode. |
| Backup server | TCP | 10006 | Used to communicate with the backup server. |
| Veeam backup repository or [gateway server](gateway_server.md) | TCP | 2500-3300 | Default range of ports used as transmission channels for jobs and restore sessions. For each TCP connection that a job uses, one port from this range is assigned. |
| 6162 | Default port used by Veeam Transport Service (on Linux servers) or Veeam Data Mover Service (on Windows servers) |
| Veeam Update Repository (repository.veeam.com)  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) (cloudfront.net, amazonaws.com) | TCP/HTTPS | 443 | Used to download worker deployment packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |
| NTP server | UDP | 123 | Used for time synchronization with NTP servers. |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

Backup Server

| From | To | Protocol | Port | Notes |
| Backup server | Worker | TCP | 19000 | Used to communicate with workers. |
| TCP/HTTPS | 443 | Used by the Platform Service to enable communication with the Veeam Updater service on the worker. |
| Backup server | TCP/HTTPS | 6172 | Used by the Platform Service to enable communication with the Veeam Backup & Replication database. |
| Xen pool | TCP/HTTPS | 443 | Used to communicate with the XAPI management service running on the Xen pool. |
| FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during file-level restore. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see [Used Ports](used_ports.md). |

Page updated 2026-07-23

