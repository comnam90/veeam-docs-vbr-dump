---
title: "Before You Begin"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_vcd_tenant_before.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you add a new VMware Cloud Director tenant account, check the following prerequisites and limitations:

* A TLS certificate must be installed on the SP Veeam backup server.

* At least one cloud gateway must be added in the Veeam Cloud Connect infrastructure on the SP backup server.

* The VMware Cloud Director Server must be added to the Veeam backup infrastructure on the SP backup server.
* The organization whose organization VDCs you plan to provide as a cloud host for tenant VM replicas must be created in VMware Cloud Director.
* The organization administrator user account must be created for the organization in VMware Cloud Director.
* Organization VDC that you plan to provide as a cloud host for tenant VM replicas must be allocated to the organization in VMware Cloud Director.
* An NSX Edge Gateway or IPsec VPN connection must be configured for the organization in VMware Cloud Director (in case you plan to use VMware Cloud Director resources to provide network access to tenant VM replicas after failover).
* Backup repositories that you plan to use as cloud repositories must be added to your backup infrastructure. When you create a tenant account, you can allocate storage resources for the tenant only on those backup repositories that are currently added to Veeam Backup & Replication.
* If tenants will work with the cloud repository and cloud host over WAN accelerators, the target WAN accelerator must be properly configured on the SP side.
* If you plan to provide network resources for VMware Cloud Director replicas, it is recommended that you change the password for the root account of network extension appliances before you create the first VMware Cloud Director tenant account in the Veeam Cloud Connect infrastructure. You can change the password using the Credentials Manager. To learn more, see [Managing Network Extension Appliance Credentials](network_extension_credentials.md).


