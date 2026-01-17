---
title: "Getting Started with CDP"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_cdp_quickstart.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Getting Started with CDP


To start using the CDP functionality in the Veeam Cloud Connect environment, the SP and tenant must perform the following tasks.

|  |
| --- |
| Note |
| Before you start using the CDP functionality in the Veeam Cloud Connect environment, consider [requirements and limitations](cloud_replication_limitations.md#cdp). |

Tasks on SP Side

To let the tenant create CDP replicas on the cloud host, the SP must complete the following steps:

1. Set up the Veeam Cloud Connect infrastructure:

1. [Deploy the SP Veeam backup server](cloud_connect_sp_vbr_deploy.md).
2. [Set up a TLS certificate](cloud_connect_manage_ssl.md).
3. [Deploy one or more cloud gateways](cloud_connect_gateways.md) or [configure a cloud gateway pool](cloud_gateway_pool_add.md).
4. [For the CDP to VMware vSphere scenario] [Allocate VLANs for cloud networking](hardware_plan_network_vlans.md).
5. [For the CDP to VMware vSphere scenario] [Allocate a pool of public IP addresses for full site failover](cloud_connect_user_public_ip.md).

This step is not required if the SP already uses Veeam Backup & Replication to provide cloud services to tenants, and the Veeam Cloud Connect infrastructure is set up on the SP side.

1. Configure replication resources for tenant CDP replicas. This operation differs depending on what resources you want to provide to the tenant as a replication target:

* [For the CDP to VMware vSphere scenario] If you want to use resources of a VMware vSphere cluster, create one or more VMware vSphere hardware plans. The process of creating a hardware plan for CDP replicas does not differ from the same process for snapshot-based replicas. For details, see [Configuring Hardware Plans](cloud_connect_configure_hardware_plan.md).
* [For the CDP to VMware Cloud Director scenario] If you want to use resources of VMware Cloud Director, create the necessary number of organization VDCs in VMware Cloud Director and add the VMware Cloud Director server to the backup infrastructure on the SP backup server. For details, see [Getting Started with Replication to VMware Cloud Director](cloud_vcloud_director_quickstart.md#cloud_director).

1. Deploy the CDP infrastructure components:

1. Deploy the target CDP proxy. For details, see the [Adding CDP Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_proxy_add.html?ver=13) section in the Veeam Backup & Replication User Guide.
2. Install the I/O filter on the VMware vSphere cluster or VMware Cloud Director organization VDC where replication resources are allocated. For details, see the [Installing I/O Filter](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_io_filter_install.html?ver=13) and [Installing I/O Filter on VDCs](https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_cdp_io_filter_install.html?ver=13) sections in the Veeam Backup & Replication User Guide.

1. Assign replication resources that you configured at the step 2 to a new or existing tenant account.

* [For the CDP to VMware vSphere scenario] Subscribe as the tenant with a standalone tenant account to a hardware plan. For details, see [Configuring Standalone Tenant Account](cloud_connect_user.md).
* [For the CDP to VMware Cloud Director scenario] In the properties of a VMware Cloud Director tenant account, select an organization VDC that will be used as a cloud host. For details, see [Configuring VMware Cloud Director Tenant Account](cloud_vcd_tenant.md).

Once the tenant account is created, the SP must pass the account credentials as well as a DNS name or IP address of the cloud gateway to the tenant.

Tasks on Tenant Side

To work with CDP replicas on the cloud host, the tenant must complete the following steps:

1. Set up the Veeam Cloud Connect infrastructure. To learn more, see [Deploying Tenant Veeam Backup Server](cloud_connect_user_vbr_deploy.md) and [Connecting Source Virtualization Hosts](cloud_connect_hypervisor_add.md).

This step is not required if the Veeam Cloud Connect infrastructure is already configured on the tenant side.

1. Deploy the CDP infrastructure components:

1. Deploy the source CDP proxy. For details, see the [Adding CDP Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_proxy_add.html?ver=13) section in the Veeam Backup & Replication User Guide.
2. [For CDP for VMware vSphere] Install the I/O filter on the VMware vSphere cluster where source hosts with production VMs reside. For details, see the [Installing I/O Filter](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_io_filter_install.html?ver=13) section in the Veeam Backup & Replication User Guide.
3. [For universal CDP] Install Veeam CDP Agent Service and Veeam CDP Volume Filter Driver on the source workloads, that is, machines for which the tenant wants to create CDP replicas. For details, see the [Installing CDP Agent Service and Filter Driver](https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_service_install.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. Add the SP in the tenant Veeam backup console using credentials of the tenant account obtained from the SP. For details, see [Connecting to Service Providers](cloud_connect_sp.md).

Alternatively, the tenant can rescan the SP. Cloud host provided to the tenant will become available as a cloud host.

* Cloud hosts that use resources provided to the tenant through a hardware plan are displayed under the VMware vSphere > VMware Cloud Hosts node of the tenant Veeam backup console.
* Cloud hosts that use resources provided to the tenant in VMware Cloud Director are displayed under the VMware Cloud Director > VMware Cloud Director Cloud Hosts node of the tenant Veeam backup console.

1. Create a CDP policy targeted at a cloud host. For details, see [Creating CDP Policies for VMware vSphere](creating_cdp_policies.md) and [Creating Universal CDP Policies](creating_universal_cdp_policies.md).
2. In case one or more VMs in the production site become unavailable, the tenant can perform failover tasks with VM replicas on the cloud host. For details, see [Performing Full Site Failover](performing_full_site_failover.md) and [Performing Partial Site Failover](performing_partial_site_failover.md).


