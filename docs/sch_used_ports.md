---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_used_ports.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Ports


Veeam Plug-in for Scale Computing HyperCore automatically creates firewall rules for the ports required to allow communication between the Scale Computing HyperCore cluster, workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Worker | Scale Computing HyperCore cluster | TCP/HTTPS | 443 | Used to communicate with the REST API service running on the Scale Computing HyperCore cluster. |
| Backup server | TCP | 10006 | Used to communicate with the backup server. |
| Veeam backup repository or [gateway server](gateway_server.md) | TCP | 2500-3300 | Default range of ports used as transmission channels for jobs and restore sessions. For each TCP connection that a job uses, one port from this range is assigned. |
| Rocky Linux repositories  (mirrors.rockylinux.org, mirrors.fedoraproject.org, rockylinux.map.fastly.net) | TCP/HTTP(S) | 80 (443) | Used to get OS security updates and .NET Core package updates.  Note: The listed mirror URLs are used to get actual URLs that will be used to obtain updates. |
| Veeam Update Repository  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) | TCP/HTTPS | 443 | Used to download worker deployment packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |
| Nginx repository  (nginx.org/packages/, nginx.org/packages/keys/) | TCP/HTTPS | 443 | Used to download Nginx packages for worker updates. |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP/HTTPS | 8547 | Used to communicate with the Platform Service REST API. |
| Backup server | Worker | TCP | 10006 | Used to communicate with workers. |
| FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during file-level restore. |
| Backup server | TCP/HTTPS | 6172 | Used by the Platform Service to enable communication with the Veeam Backup & Replication database. |
| Scale Computing HyperCore cluster | TCP/HTTPS | 443 | Used to communicate with the REST API service running on the Scale Computing HyperCore cluster. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see section [Used Ports](used_ports.md). |


