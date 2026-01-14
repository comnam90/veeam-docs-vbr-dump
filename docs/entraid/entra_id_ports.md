---
title: "Ports"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_ports.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# Ports

In this article

The main ports required to create backups of Microsoft Entra ID tenants are listed in the following table.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 9419 | Default port for communication with REST API service. |
| Backup server | TCP | 443 | Port used by the Veeam Backup & Replication console to communicate with the backup server. |
| Backup server | PostgreSQL server hosting the database for the Microsoft Entra ID backup repository | TCP | 5432 | Default port used for communication with PostgreSQL server on which the database for Microsoft Entra ID backup repository is located.  Note: This port is required if the database is located on a remote PostgreSQL server. Port number may differ if you configure a custom PostgreSQL server instance as Microsoft Entra ID backup repository. |
| Proxy server | TCP | 3128 | Port used by Veeam Backup & Replication to redirect traffic to Microsoft Azure services through a proxy server.  Note: This port is required if you configure a proxy server as described in Veeam Backup & Replication User Guide, section [Configuring HTTP/HTTPS Proxies](https://helpcenter.veeam.com/docs/vbr/em/hmc_configure_proxies.html?ver=13). |
| Microsoft Entra ID Services | TCP | 443 | Management and data transport port required for communication with Microsoft Azure.  Note: To access the necessary Azure service, you can use the IP address, DNS name or [virtual network service tag](https://learn.microsoft.com/en-us/azure/virtual-network/service-tags-overview) of the service. If you want to use an IP address, you can download a .JSON file with the full list of Azure IP ranges and service tags from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519). |
| Azure Resource Manager | TCP | 443 |
| [Optional] Proxy server | Microsoft Entra ID Services (Service tag: AzureActiveDirectory) | TCP | 443 | Management and data transport port required for communication with Microsoft Azure though a proxy server.  Note: To access the necessary Azure service, you can use the IP address, DNS name or [virtual network service tag](https://learn.microsoft.com/en-us/azure/virtual-network/service-tags-overview) of the service. If you want to use an IP address, you can download a .JSON file with the full list of Azure IP ranges and service tags from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519). |
| Azure Resource Manager (Service tag: AzureResourceManager) | TCP | 443 |

|  |
| --- |
| Important |
| As Veeam Backup for Microsoft Entra ID is installed on the same machine where Veeam Backup & Replication runs, it also uses the same [ports](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13#backup-server).  To be able to use the log backup, log backup copy and tenant backup copy features, you must configure the ports listed in the [Cache Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?zoom_highlight=cache+proxy&ver=13#cache-repository-connections) and [Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13#backup-repositories) sections of the Veeam Backup & Replication User Guide. |

Page updated 12/19/2025

Page content applies to build 13.0.1.1071
