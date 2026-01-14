---
title: "cloud_connect_user_before"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user_before.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

Before you add a new tenant account, check the following prerequisites:

* A TLS certificate must be installed on the SP Veeam backup server.

* At least one cloud gateway must be added in the Veeam Cloud Connect infrastructure on the SP backup server.

* Backup repositories that you plan to use as cloud repositories must be added to your backup infrastructure. When you create a tenant account, you can allocate storage resources for the tenant only on those backup repositories that are currently added to Veeam Backup & Replication.
* Hardware plans that you plan to provide to a tenant must be configured in your Veeam Cloud Connect infrastructure. When you create a tenant account, you can subscribe the tenant only to those hardware plans that are currently configured in Veeam Backup & Replication.
* You can subscribe one tenant to several hardware plans that utilize resources of the same virtualization platform — VMware vSphere or Microsoft Hyper-V. To make it possible for the tenant to replicate VMware and Hyper-V VMs simultaneously, the SP must create two different tenant accounts for the same tenant.
* If tenants will work with the cloud repository and cloud host over WAN accelerators, the target WAN accelerator must be properly configured on the SP side.
* It is recommended that you change the password for the root account of network extension appliances before subscribing tenants to hardware plans. You can change the password using the Credentials Manager. To learn more, see [Managing Network Extension Appliance Credentials](network_extension_credentials.md).

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
