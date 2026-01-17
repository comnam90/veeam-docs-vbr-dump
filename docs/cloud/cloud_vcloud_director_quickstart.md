---
title: "Getting Started with Replication to VMware Cloud Director"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_vcloud_director_quickstart.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---


In this article

The SP and tenant can use VMware Cloud Director resources as a target for snapshot-based replication and CDP. Within the Veeam Cloud Connect Replication to VMware Cloud Director scenario, the SP and tenant perform the following tasks.

Tasks on SP Side

To let the tenant create snapshot-based replicas or CDP replicas on a cloud host that uses VMware Cloud Director resources as a back end, the SP must complete the following steps:

1. Configure replication target resources in VMware Cloud Director:

1. Create a VMware Cloud Director organization.
2. Create a user account with administrative rights in the organization. The tenant will use the credentials of this account to connect to the SP. To learn more, see [VMware Cloud Director Tenant Account](cloud_vcloud_director_tenant.md).
3. Create one or more organization VDCs that will be used as cloud hosts for tenant VM replicas.
4. Configure an NSX Edge gateway and IPsec VPN connection to enable network access to tenant VM replicas.

An NSX Edge gateway provides network access to VM replicas in VMware Cloud Director after partial site failover and full site failover.

An IPsec VPN connection may be used to provide network access to tenant VM replicas after partial site failover. Alternatively, the SP can choose to use the network extension appliance for partial site failover.

To learn more, see [Network Resources for VMware Cloud Director Replicas](cloud_vcloud_director_infrastructure.md).

For information about how to perform these tasks, refer to the VMware Cloud Director documentation.

|  |
| --- |
| Note |
| The SP must disable VM discovery in VMware Cloud Director that is used to allocate replication resources for tenants. |

1. Configure Veeam Cloud Connect infrastructure in Veeam Backup & Replication:

1. Deploy the SP backup server. For details, see [Deploying SP Veeam Backup Server](cloud_connect_sp_vbr_deploy.md).
2. Set up a TLS certificate. For details, see [Managing TLS Certificates](cloud_connect_manage_ssl.md).
3. Deploy one or more cloud gateways or cloud gateway pools. For details, see [Adding Cloud Gateways](cloud_connect_gateways.md) and [Configuring Cloud Gateway Pools](cloud_gateway_pool_add.md).
4. Add the VMware Cloud Director server to the backup infrastructure on the SP backup server. For details, see the [Adding VMware Cloud Director Servers](https://helpcenter.veeam.com/docs/vbr/userguide/adding_vcloud_director.html?ver=13) section in the Veeam Backup & Replication User Guide.
5. Deploy the necessary number of target backup proxies: VMware backup proxies (for snapshot-based replication) or CDP proxies (for CDP). For details, see the [Adding VMware Backup Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/add_vmware_proxy.html?ver=13) and [Adding CDP Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_proxy_add.html?ver=13) sections in the Veeam Backup & Replication User Guide.
6. [For CDP] Install the I/O filter on organization VDCs that will be used as cloud hosts for tenant VM replicas. This operation does not differ from the VMware Cloud Director CDP scenario in the regular Veeam Backup & Replication infrastructure. For details, see the [Installing I/O Filter on VDCs](https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_cdp_io_filter_install.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| If you add a new organization VDC to the Cloud Director server after the I/O filter is installed on the existing VDCs, you must do the following:   1. Install the I/O filter on the newly added organization VDC. To do this, at the Organization VDC step of the I/O Filter Management wizard, select check boxes next to the VDC where the I/O filter must be present and finish the wizard. For details, see the [Select VDC Organizations](https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_io_filter_vdc.html?ver=13) section in the Veeam Backup & Replication User Guide. 2. Update properties of the cloud gateway through which the tenant who will use the newly added VDC connects to the SP. To do this, launch the Edit Cloud Gateway wizard for this cloud gateway, click Next at each step of the wizard and then click Finish at the Summary step of the wizard.   Once the SP completes these steps, the tenant can rescan the SP in the tenant Veeam backup console and start using the newly added VDC as a cloud host. |

1. Create VMware Cloud Director tenant account and assign to this tenant account replication resources that use an organization VDC as a back end. For details, see [Configuring VMware Cloud Director Tenant Account](cloud_vcd_tenant.md).

|  |
| --- |
| Note |
| Steps a–c are not required if the SP already uses Veeam Backup & Replication to provide cloud services to tenants, and the Veeam Cloud Connect infrastructure is set up on the SP side. |

Tasks on Tenant Side

To create snapshot-based replicas or CDP replicas on a cloud host that uses VMware Cloud Director resources as a back end, the tenant must complete the following steps:

1. Set up the Veeam Cloud Connect infrastructure. For details, see [Deploying Tenant Veeam Backup Server](cloud_connect_user_vbr_deploy.md) and [Connecting Source Virtualization Hosts](cloud_connect_hypervisor_add.md).

This step is not required if the Veeam Cloud Connect infrastructure is already configured on the tenant side.

1. Deploy the necessary number of source backup proxies: VMware backup proxies (for snapshot-based replication) or CDP proxies (for CDP). For details, see the [Adding VMware Backup Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/add_vmware_proxy.html?ver=13) and [Adding CDP Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_proxy_add.html?ver=13) sections in the Veeam Backup & Replication User Guide.
2. [For CDP] Install the I/O filter on the VMware vSphere cluster where tenant VMs reside. This operation does not differ from the CDP scenario in the regular Veeam Backup & Replication infrastructure. For details, see the [Installing I/O Filter](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_io_filter_install.html?ver=13) section in the Veeam Backup & Replication User Guide.
3. Add the SP in the tenant Veeam backup console using credentials of the VMware Cloud Director organization administrator account. For details, see [Connecting to Service Providers](cloud_connect_sp.md).
4. Depending on the required RPO, create a replication job or CDP policy targeted at a cloud host that uses an organization VDC as a back end. For details, see [Creating Replication Jobs](creating_replication_jobs.md) and [Creating CDP Policies](creating_cdp_policies.md).
5. In case one or more VMs in the production site become unavailable, the tenant can perform failover tasks with VM replicas on the cloud host. To learn more, see [Performing Full Site Failover](performing_full_site_failover.md) and [Performing Partial Site Failover](performing_partial_site_failover.md).

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
