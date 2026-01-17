---
title: "Network Resources for VMware Cloud Director Replicas"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_vcloud_director_infrastructure.html"
last_updated: "1/26/2024"
product_version: "13.0.1.1071"
---


In this article

To allow tenant VM replicas created in VMware Cloud Director to communicate to each other after partial site failover or full site failover, the SP must configure the necessary number of networks in the properties of the organization VDC that will be used as a target for tenant VM replicas. The tenant will be able to map source and target networks in the properties of the replication job that creates VM replicas in VMware Cloud Director.

In addition, the SP must provide tenant VM replicas in VMware Cloud Director with network resources that enable access to VM replicas over the network:

* From the production environment on the tenant side after partial site failover. To learn more, see [Network Resources for Partial Site Failover](#vcd_partial_failover).

* From the internet after full site failover. To learn more, see [Network Resources for Full Site Failover](#vcd_full_failover).

|  |
| --- |
| Note |
| Consider the following:   * The process of allocating network resources for VM replicas in VMware Cloud Director differs from the same process for VM replicas created on a cloud host provided to a tenant through a hardware plan. In the regular Veeam Cloud Connect Replication scenario, network resources for tenant VM replicas are provided through VLANs and public IP addresses reserved in the Veeam Cloud Connect infrastructure. For more information, see [Veeam Cloud Connect Replication](cloud_replication.md). * Veeam Backup & Replication does not map source networks to which production VMs are connected to isolated vApp networks in VMware Cloud Director. |

Network Resources for Partial Site Failover

There are three scenarios for enabling communication between production VMs on the tenant source host and VM replicas in VMware Cloud Director after partial site failover:

* Using the NSX Edge gateway. In this scenario, the SP deploys the NSX Edge gateway on the SP side and tenant side and configures the NSX edge gateway in VMware Cloud Director. This scenario does not require additional actions in Veeam Backup & Replication.
* Using an IPsec VPN connection. In this scenario, the SP configures an IPsec VPN connection between the tenant side and SP side. This operation is performed in VMware Cloud Director. This scenario does not require additional actions in Veeam Backup & Replication.
* Using network extension appliances. In this scenario, the SP does not use VMware Cloud Director resources to enable network access to tenant VM replicas. Instead, the SP and tenant deploy network extension appliances on their sides in the similar way as in the regular Veeam Cloud Connect Replication scenario:

* The SP deploys the SP-side network extension appliance at the process of creating a VMware Cloud Director tenant account. To learn more, see [Configuring VMware Cloud Director Tenant Account](cloud_vcd_tenant.md).
* The tenant deploys the tenant-side network extension appliance at the process of adding the SP in the Veeam backup console. To learn more, see [Connecting to Service Providers](cloud_connect_sp.md).

For the scenario where production VMs and VM replicas in VMware Cloud Director communicate through network extension appliances after partial site failover, consider the following:

* To provide network resources to tenant VM replicas, the SP should use isolated organization VDC networks.
* The Enable DHCP option must be disabled for organization VDC networks that will be used by tenant VM replicas. This operation can be performed by the SP or tenant in VMware Cloud Director.
* In case Veeam Backup & Replication fails to detect a static IP address of a tenant VM during the replication process, the SP or tenant must manually specify the IP address for the replica of this VM in VMware Cloud Director. In particular, Veeam Backup & Replication cannot detect an IP address of a Linux VM.
* During partial-site failover, the SP network extension appliance imports in its vApp all organization VDC networks and connects to these networks. This allows the appliance to provide network connection to VM replicas that reside in other vApps of the organization VDC used as a cloud host, including those replicas for which the failover operation can be started later.

Keep in mind that if the number of organization VDC networks is greater than 9, the failover operation will fail because the number of virtual network adapters for a VMware vSphere VM cannot exceed 10 (one network adapter is used to connect to the management network).

Network Resources for Full Site Failover

To allow tenant VM replicas in VMware Cloud Director to be accessed over the internet, the SP must configure an NSX Edge gateway in VMware Cloud Director.

To assign public IP addresses to tenant VM replicas after full site failover, the SP can create SNAT and DNAT rules on the NSX Edge gateway. Alternatively, the SP can assign public IP addresses to tenant VM replicas using pre-failover and post-failover scripts. To do this, the SP must create the scripts in advance and specify these scripts in the cloud failover plan settings.

|  |
| --- |
| Note |
| In contrast to the regular Veeam Cloud Connect Replication scenario, the SP cannot use network extension appliances to enable access to VM replicas in VMware Cloud Director after full site failover. |

Page updated 1/26/2024

Page content applies to build 13.0.1.1071
