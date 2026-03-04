---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_used_ports.html"
last_updated: "3/3/2026"
product_version: "13.0.1.1071"
---

# Ports


Veeam Backup & Replication automatically creates firewall rules for the ports required to allow communication between the HPE Morpheus VM Essentials manager, workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

Workers

| From | To | Protocol | Port | Notes |
| Worker | HPE Morpheus VM Essentials manager | TCP/HTTPS | 443 | Used to communicate with the REST API service running on the HPE Morpheus VM Essentials manager. |
| HPE Morpheus VM Essentials manager | TCP | 7433 | Used to communicate with HPE Morpheus VM Essentials manager clusters when using the NBD transport mode and executing libvirt commands. |
| Veeam backup repository or [gateway server](gateway_server.md) | TCP | 6162 | Default range of ports used as transmission channels for jobs and restore sessions. For each TCP connection that a job uses, one port from this range is assigned. |
| Backup server | TCP | 2500 to 3300 | Default range of ports used for ransomware index transfer. |
| Veeam Update Repository (repository.veeam.com)  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) (cloudfront.net, amazonaws.com) | TCP/HTTPS | 443 | Used to download worker deployment packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |
| Veeam Update Repository (local mirror)  (<yourlocalmirror.domain>) | TCP | 443 or 80 | Used to download worker update packages from your local mirror repository if enabled as described in section [Setting Up Global Update Configuration](update_appliance_configure_updates.md#global_configuration). |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

Backup Server

| From | To | Protocol | Port | Notes |
| Backup server | Worker | TCP | 19000 | Used to communicate with workers. |
| Worker | TCP/HTTPS | 443 | Used by the Platform Service to enable communication with the Veeam Updater service on the worker. |
| HPE Morpheus VM Essentials manager | TCP/HTTPS | 443 | Used to communicate with the REST API service running on the HPE Morpheus VM Essentials manager. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see [Ports](used_ports.md). |


