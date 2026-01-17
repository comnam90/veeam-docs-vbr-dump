---
title: "Getting Started with Veeam Cloud Connect Replication"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_replication_getting_started.html"
last_updated: "9/17/2025"
product_version: "13.0.1.1071"
---


In this article

To provide Disaster Recovery as a Service through image-based VM replication to tenants, the SP must set up the Veeam Cloud Connect Replication infrastructure.

Before the SP starts configuring the Veeam Cloud Connect Replication infrastructure, they must consider limitations for hardware plans. Limitations apply to virtualization hosts whose resources the SP plans to expose as a replication target to tenants. To learn more, see [Adding Hardware Plans: Before You Begin](hardware_plan_before_you_begin.md).

As part of the configuration process, the SP must perform the following tasks:

1. [Deploy the SP Veeam backup server](cloud_connect_sp_vbr_deploy.md).
2. [Set up TLS certificates](cloud_connect_manage_ssl.md).
3. [Create cloud gateways](cloud_connect_gateways.md).
4. [Allocate VLANs for cloud networking](hardware_plan_network_vlans.md).
5. [Allocate a pool of public IP addresses for full site failover](cloud_connect_user_public_ip.md).
6. [Configure hardware plans](cloud_connect_configure_hardware_plan.md).
7. [Specify credentials for network extension appliances](network_extension_credentials.md).
8. [Optional] [Configure target WAN accelerators](cloud_connect_configure_wan.md).
9. [Create tenant accounts](cloud_connect_tenant.md).
10. [Communicate information about the tenant account and gateway to all tenants who plan to connect to the SP](cloud_connect_user_next.md).

|  |
| --- |
| Note |
| The SP can also allocate VMware Cloud Director resources as replication resources to the tenant. To learn more, see [VMware Cloud Director Support](cloud_vcloud_director.md). |

Once the SP has configured necessary components, tenants can add the SP to their Veeam Backup & Replication consoles and use cloud hosts allocated to them in the SP Veeam Cloud Connect infrastructure.

Related Concepts

* [Veeam Cloud Connect Replication](cloud_replication.md)
* [Veeam Cloud Connect Infrastructure](cloud_infrastructure.md)

Page updated 9/17/2025

Page content applies to build 13.0.1.1071
