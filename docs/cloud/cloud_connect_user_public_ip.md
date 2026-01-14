---
title: "cloud_connect_user_public_ip"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user_public_ip.html"
last_updated: "11/9/2023"
product_version: "13.0.1.1071"
---


In this article

It may be required that one or several replica VMs should be accessible from the internet after full site failover. To accomplish this, all VM replicas on the cloud host that need to be accessed from the internet must have public IP address.

With Veeam Backup & Replication, the SP can allocate in their network infrastructure a pool of public IP addresses and provide one or several public IP addresses from this pool to the tenant. The tenant can specify public IP addressing settings at the process of the cloud failover plan configuration.

When the tenant production VM fails over to its replica on the cloud host during full site failover, Veeam Backup & Replication assigns a specified public IP address to the network extension appliance on the SP side. The network extension appliance redirects traffic from this public IP address to the IP address of a VM replica in the internal VM replica network. As a result, a VM replica on the cloud host can be accessed from the internet.

To allocate a pool of public IP addresses, the SP can specify individual IP addresses or IP address ranges. The SP can add to the pool both IPv4 and IPv6 addresses.

Consider the following:

* The SP does not need to allocate public IP addresses in Veeam Backup & Replication if the SP uses VMware Cloud Director to provide replication resources to tenants. Instead, the SP configures the NSX Edge gateway in the properties of the organization VDC that will be used as a cloud host for tenant VM replicas.
* To enable access to a tenant VM replica by a public IP address, the SP must properly configure port forwarding to the SP network extension appliance in the production network infrastructure.
* It is recommended that the SP plans network resource allocation and allocates public IP addresses in advance. However, the SP can also create or edit a pool of available public IP addresses when subscribing a tenant to a hardware plan. To learn more, see [Specify Network Extension Settings](cloud_connect_user_network_failover.md).

Related Tasks

* [Managing IPv4 Addresses](cloud_connect_public_ipv4.md)
* [Managing IPv6 Addresses](cloud_connect_public_ipv6.md)

Page updated 11/9/2023

Page content applies to build 13.0.1.1071
