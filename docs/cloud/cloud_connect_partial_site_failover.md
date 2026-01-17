---
title: "Partial Site Failover"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_partial_site_failover.html"
last_updated: "11/9/2023"
product_version: "13.0.1.1071"
---

# Partial Site Failover


If one or several production VMs become corrupted, but the rest of the production site, including the most critical VMs and Veeam Backup & Replication infrastructure, remain operative, the tenant can perform partial site failover. With partial site failover, the tenant can quickly recover a corrupted VM by failing over to its replica on the cloud host.

To establish a secure connection and enable communication between production VMs and VM replicas on the cloud host after partial site failover, Veeam Backup & Replication uses paired network extension appliances deployed on the tenant side and SP side. To learn more, see [Network Extension Appliance](cloud_network_extension_appliance.md).

Partial site failover is performed in the similar way as regular failover. However, the partial site failover process contains several additional steps regarding the use of network extension appliances on the tenant side and SP side:

1. The tenant starts the partial site failover process for a VM in the tenant Veeam Backup & Replication console.
2. Veeam Backup & Replication rolls back the VM replica on the cloud host to the required restore point. To do this, it reverts the VM replica to the necessary snapshot in the replica chain.
3. Veeam Backup & Replication powers on the VM replica. The state of the VM replica is changed from Normal to Failover. If the original VM still exists and is running, the original VM remains powered on.
4. Veeam Backup & Replication powers on the network extension appliance VM on the cloud host and configures network settings on the appliance:

* Starts a VPN server on the network extension appliance to establish a secure VPN tunnel through the cloud gateway to the appliance on the tenant side.
* Configures Proxy ARP daemon on the appliance so that the appliance can receive from the VM replica ARP requests addressed to production VMs on the source host and send them to the tenant network extension appliance through the VPN tunnel.

1. Veeam Backup & Replication temporarily puts replication activities for the original VM on hold (until the VM replica returns to the Normal state).
2. Veeam Backup & Replication powers on the network extension appliance on the tenant side and configures network settings on the appliance:

* Starts a VPN client on the network extension appliance and connects to the VPN server on the network extension appliance on the SP side to establish a secure VPN tunnel through the cloud gateway.
* Configures Proxy ARP daemon on the network extension appliance so that it can receive ARP requests from production VMs addressed to the VM replica and send them to the network extension appliance on the SP side through the VPN tunnel.

1. All changes made to the VM replica while it is running in the Failover state are written to the delta file of the snapshot, or restore point, to which you have selected to roll back.
2. VMs on the tenant side communicate to the VM replica on the cloud host through the secure VPN tunnel that is set between network extension appliances.

![Partial Site Failover](images/cloud_failover_partial.webp)

Limitations for Partial Site Failover

Partial site failover has the following limitations:

* Veeam Backup & Replication supports one failover operation type at a time. If a tenant or the SP runs a cloud failover plan during partial site failover, Veeam Backup & Replication will suggest that the VM involved in the partial site failover process is processed with the cloud failover plan.
* The tenant can perform partial site failover only for those VMs that have a static IP address.

Related Topics

[Network Mapping for Cloud Replicas](cloud_network_mapping.md)

Related Tasks

[Performing Partial Site Failover](performing_partial_site_failover.md)


