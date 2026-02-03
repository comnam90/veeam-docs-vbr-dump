---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_used_ports.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Ports


Veeam Plug-in for oVirt KVM automatically creates firewall rules for the ports required to allow communication between the workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Worker | Backup server | TCP | 19000 | Used to communicate with the Veeam Backup & Replication server. |
| oVirt KVM Manager | TCP/HTTPS | 443 | Used to communicate with the REST API service running on the oVirt KVM Manager. |
| oVirt KVM Manager | TCP | 54323 | Used to communicate with oVirt KVM Manager (hosted engine). |
| oVirt KVM host | TCP | 54322 | Used to communicate with oVirt KVM hosts. |
| Veeam backup repository or [gateway server](gateway_server.md) | TCP | 2500-3300 | Default range of ports used as transmission channels for jobs and restore sessions. For each TCP connection that a job uses, one port from this range is assigned. |
| Veeam Update Repository  (repository.veeam.com, cloudfront.net) | TCP/HTTPS | 443 | Used to download worker update packages. |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP/HTTPS | 443 | Used to communicate with the Platform Service REST API. |
| Backup server | FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during file-level restore. |
| Backup server | TCP/HTTPS | 6172 | Used by the Platform Service to enable communication with the Veeam Backup & Replication database. |
| oVirt KVM Manager | TCP/HTTPS | 443 | Used to communicate with the REST API service running on the oVirt KVM Manager. |
| oVirt KVM Manager | TCP | 54323 | Used to communicate with the oVirt KVM Manager (hosted engine). |
| oVirt KVM host | TCP | 54322 | Used to communicate with oVirt KVM hosts. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see [Ports](https://helpcenter.veeam.com/docs/backup/vsphere/used_ports.html?ver=120#backup-repositories). |


