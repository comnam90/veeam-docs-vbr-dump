---
title: "Step 5. Allocate Replication Resources"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user_compute_resources.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

The Replica Resources step of the wizard is available if you selected the Replication resources option at the [Tenant](cloud_connect_user_settings.md) step of the wizard. You can use this step to subscribe the created tenant account to the hardware plan.

To subscribe a tenant to a hardware plan:

1. Click Add on the right of the Hardware plans list and select VMware or Hyper-V.
2. From the Select hardware plan list in the Add replication resource window, select a hardware plan to which you want to subscribe the tenant.
3. [For tenants who plan to use WAN accelerators] Select the Enable WAN acceleration through the following WAN accelerator check box and choose a target WAN accelerator configured at the SP side. The source WAN accelerator is configured on the tenant side. The tenant will select the source WAN accelerator on their side when configuring a replication job.
4. Click OK.
5. Repeat steps 1–4 for all hardware plans to which you want to subscribe the tenant.
6. Select the Use Veeam network extension capabilities during partial and full site failover option to allocate network resources for performing failover tasks. With this option enabled, the New Tenant wizard will include the additional [Network Extension](cloud_connect_user_network_failover.md) step.
7. To configure range of VLANs that will be used for providing isolated IP networks for tenant VM replicas on the cloud host, click the Manage network settings link. Then use the VLANs Configuration window to specify the necessary number of VLANs on the virtualization host that provides resources for the hardware plan to which the tenant is subscribed. To learn more, see [Managing VLANs](hardware_plan_network_vlans.md).

![Step 5. Allocate Replication Resources](images/add_user_replica_resources.webp)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
