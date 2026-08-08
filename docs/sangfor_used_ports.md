---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_used_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Ports


Veeam Backup & Replication automatically creates firewall rules for the ports required to allow communication between the Sangfor aSV server, workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

Workers

| From | To | Protocol | Port | Notes |
| Worker | Sangfor aSV server | TCP/HTTPS | 4430 | Used to communicate with the REST API service running on the Sangfor aSV server. |
| 443 | Used by the worker for NBD/NBDSSL data transport when HotAdd is not available. |
| Backup server | TCP | 10006 | Used to communicate with the backup server. |
| Veeam backup repository or [gateway server](gateway_server.md) | TCP | 6162 | Default port used as transmission channel for jobs and restore sessions. |
| Veeam Update Repository (repository.veeam.com)  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) (cloudfront.net, amazonaws.com) | TCP/HTTPS | 443 | Used to download worker deployment packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |
| NTP server | UDP | 123 | Used for time synchronization with NTP servers. |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

Backup Server

| From | To | Protocol | Port | Notes |
| Backup server | Worker | TCP | 19000 | Used to communicate with workers. |
| Worker | TCP/HTTPS | 443 | Used by the Platform Service to enable communication with the Veeam Updater service on the worker. |
| Backup server | TCP/HTTPS | 6172 | Used by the Platform Service to enable communication with the Veeam Backup & Replication database. |
| Sangfor aSV server | TCP/HTTPS | 4430 | Used to communicate with the REST API service running on the Sangfor aSV server. |
| FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during file-level restore. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see [Ports](used_ports.md). |

Page updated 2026-07-16

