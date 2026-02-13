---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_used_ports.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Ports


Veeam Backup & Replication automatically creates firewall rules for the ports required to allow communication between workers and the backup server.

Workers

The following table describes network ports that must be opened to ensure proper communication of workers with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Worker | Nutanix Prism Central and standalone clusters | TCP/HTTPS | 9440 | Used to communicate with Nutanix AHV REST API (clusters and Prism Central). |
| Backup server | TCP | 10006 | Used to connect to Veeam Backup & Replication. |
| Backup server | TCP | 2500 to 3300 | Default range of ports used for ransomware index transfer. |
| Nutanix AHV server | TCP/iSCSI | 3205, 3260 | Used to access disks attached to Nutanix AHV VMs. |
| Veeam backup repository (or [gateway server](gateway_server.md)) | TCP | 2500-3300 | Default range of ports used as transmission channels for jobs and restore sessions. For every TCP connection that a job uses, one port from this range is assigned. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Veeam Update Repository  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) (cloudfront.net, amazonaws.com) | TCP/HTTPS | 443 | Used to download worker update packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |
| Veeam Update Repository (local mirror)  (<yourlocalmirrorrepository.domain>) | TCP | 443 or 80 | Used to download worker update packages from your local mirror repository if enabled as described in section [Setting Up Global Update Configuration](update_appliance_configure_updates.md#global_configuration). |

Backup Server

The following table describes network ports that must be opened to ensure proper communication of the backup server with other backup infrastructure components specific for Veeam Plug-in for Nutanix AHV.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Worker | TCP | 19000 | Used to communicate with workers. |
| Worker | TCP/HTTPS | 443 | Used by the Platform Service to enable communication with the Veeam Updater service on the worker. |
| Nutanix AHV cluster | TCP/HTTPS | 9440 | Used by the Platform Service to connect to a Nutanix AHV cluster. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with other backup infrastructure components, see [Ports](used_ports.md). |

vPower NFS Service

The vPower NFS Service is a Microsoft Windows service that runs on a Microsoft Windows machine and enables this machine to act as an NFS server. The vPower NFS Service is required to perform such operations as file-level restore and Instant Recovery.

|  |
| --- |
| Note |
| For the full list of ports required for [Performing File-Level Restore](ahv_restoring_guest_os_files.md), see [Ports](used_ports.md). |

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Nutanix AHV cluster | Microsoft Windows server with the mount server role running vPower NFS Service | TCP  UDP | 111 | Used by the Port Mapper service. |
| TCP  UDP | 1058+ or 1063+ | Used as default mount port. The number of port depends on where the vPower NFS Service is located:   * 1058+: If the vPower NFS Service is located on the backup server. * 1063+: If the vPower NFS Service is located on a separate Microsoft Windows machine.   If port 1058/1063 is occupied, the succeeding port numbers will be used. |
| TCP  UDP | 2049+ | Used as NFS port. If port 2049 is occupied, the succeeding port numbers will be used. |


