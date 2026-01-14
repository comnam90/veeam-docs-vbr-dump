---
title: "hardware_plan_before_you_begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/hardware_plan_before_you_begin.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

Before you add a new hardware plan, check the following prerequisites:

1. A TLS certificate must be installed on the SP Veeam backup server.
2. Virtualization hosts that will provide resources to tenants through a hardware plan must be added to the backup infrastructure.
3. The process of configuring a hardware plan differs depending on virtualization environment — VMware vSphere or Microsoft Hyper-V. Thus, separate wizards are used to configure hardware plans for different virtualization environments:

* The New VMware Hardware Plan wizard — to configure a VMware hardware plan.
* The New Hyper-V Hardware Plan wizard — to configure a Hyper-V hardware plan.

The description of a hardware plan setup process is illustrated primarily with the figures from the New VMware Hardware Plan wizard. However, all the described steps except for those specified, are the same for configuring both VMware and Hyper-V hardware plans.

1. It is recommended that you plan network resources in advance and configure a range of VLANs that will be reserved for Veeam Cloud Connect Replication before configuring a hardware plan. To learn more, see [Managing VLANs](hardware_plan_network_vlans.md).

Limitations for VMware Hardware Plans

To configure a VMware hardware plan that will use resources of a vCenter Server cluster, you must use the Enterprise or Enterprise Plus edition of the VMware vSphere infrastructure. DRS functionality must be enabled on the vCenter Server cluster. Standard VMware vSphere edition does not support creating resource pools in clusters.

This limitation does not apply to standalone ESXi hosts managed by vCenter Server.

Limitations for Hyper-V Hardware Plans

Before you add a new Hyper-V hardware plan, consider the following limitations:

* Standalone Hyper-V hosts that run Nano Server installations of the Microsoft Windows Server 2016 OS cannot be used for configuring hardware plans.
* The following types of Hyper-V clusters are not supported for exposing resources through hardware plans:

* Clusters with server nodes that run Nano Server installations of the Microsoft Windows Server 2016 OS
* Clusters with the Cluster Operating System Rolling Upgrade feature enabled
* Multi-domain and Workgroup Clusters

* After you subscribe a tenant to a Hyper-V hardware plan, you cannot rename the virtual switch in Microsoft Hyper-V infrastructure that is used by VM replicas. If you rename the virtual switch, replication jobs targeted at the cloud host that use the renamed virtual switch will fail.
* Usage of a Microsoft SMB3 shared folder as a storage for VM replicas is not supported in the Veeam Cloud Connect infrastructure.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
