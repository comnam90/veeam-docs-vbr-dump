---
title: "Integrating High Availability Cluster with Veeam Products"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_integration.html"
last_updated: "4/2/2026"
product_version: "13.0.1.2067"
---

# Integrating High Availability Cluster with Veeam Products


You can integrate the HA cluster with various Veeam products to enhance monitoring, management, and recovery operations.

To perform the integration, follow these steps:

1. [Assemble the High Availability cluster](high_availability_configuration.md).
2. Add the HA cluster to the environment of the necessary Veeam product:

* Veeam ONE — Use the IP address or hostname of the primary node when you configure connections to backup servers in Veeam ONE Web Client. For detailed instructions, see the [Connecting Veeam Backup & Replication Servers](https://helpcenter.veeam.com/docs/one/userguide/backup_server_name.html?ver=13) section in the Veeam ONE User Guide.
* Veeam Enterprise Manager — Use the virtual IP address or the full DNS name of the HA cluster when adding a backup server to Enterprise Manager. For detailed instructions, see the [Adding Backup Server](https://helpcenter.veeam.com/docs/vbr/em/adding_backup_server.html?ver=13#adding-backup-server) section in the Veeam Backup Enterprise Manager Guide.
* Veeam Recovery Orchestrator — Use the virtual IP address or full DNS name of the HA cluster when you deploy an Orchestrator agent on a remote Veeam Backup & Replication server. For detailed instructions, see the [Connecting Veeam Backup & Replication Servers](https://helpcenter.veeam.com/docs/vro/userguide/connecting_backup_servers.html?ver=13) section in the Veeam Recovery Orchestrator 13 User Guide.
* Veeam Service Provider Console — Connect primary and secondary nodes of the HA cluster to Veeam Service Provider Console. For detailed instructions, see the [Managing Backup High Availability Clusters](https://helpcenter.veeam.com/docs/vac/provider_admin/vbr_ha_clusters.html?ver=9.1) in the Veeam Service Provider Console Guide for Service Providers.

Creating High Availability Cluster Using Nodes Already Integrated with Another Veeam Product

If the Veeam Software Appliance you plan to use as a node of the HA cluster is currently part of another Veeam product infrastructure, you must remove this Veeam Software Appliance from the existing product infrastructure. After that, you can configure the HA cluster.

1. Remove from Veeam products any backup server that you plan to use as a node of the HA cluster.

|  |
| --- |
| Note |
| You do not need to remove a backup server that you plan to use as a primary node from Veeam Service Provider Console (VSPC). After you assemble the HA cluster, VSPC will automatically detect that it is now part of a cluster. In this case, you need to add the secondary node if it has not been added previously. |

1. [Assemble the HA cluster](high_availability_configuration.md).
2. Integrate the HA cluster with the necessary Veeam products.


