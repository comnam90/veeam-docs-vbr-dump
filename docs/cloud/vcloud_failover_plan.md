---
title: "Creating Cloud Failover Plans for Replicas in VMware Cloud Director"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/vcloud_failover_plan.html"
last_updated: "7/26/2023"
product_version: "13.0.1.1071"
---


In this article

If you have a number of VMs running interdependent applications, you need to fail over them one by one, as a group. To do this automatically, you can prepare a cloud failover plan.

The process of creating a cloud failover plan for VMs whose replicas reside in VMware Cloud Director differs from the regular one. The difference is that you do not need to specify default gateway settings and public IP addressing rules for such VMs. Network resources required to provide access to VM replicas from the internet after full site failover are managed by the SP in VMware Cloud Director.

Before creating a cloud failover plan, [check prerequisites](cloud_failover_plan_byb.md). Then use the Cloud Failover Plan wizard to create a cloud failover plan.

1. [Launch the Cloud Failover Plan wizard](cloud_failover_plan_launch.md).
2. [Specify the failover plan name and description](cloud_failover_plan_name.md).
3. [Select virtual machines](cloud_failover_plan_vms.md).
4. [Finish working with the wizard](cloud_failover_plan_summary.md).

Related Concepts

[Cloud Failover Plan](cloud_failover_plan_overview.md)

Page updated 7/26/2023

Page content applies to build 13.0.1.1071
