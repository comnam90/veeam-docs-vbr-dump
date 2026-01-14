---
title: "cloud_connect_configure_hardware_plan"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_configure_hardware_plan.html"
last_updated: "10/3/2023"
product_version: "13.0.1.1071"
---


In this article

To expose cloud hosts to tenants, you must configure one or more hardware plans in the Veeam Cloud Connect infrastructure.

A hardware plan is a set of computing, storage and network resources in the SP virtualization environment that the SP can expose as a target for tenant VM replicas. When the SP creates a tenant account, the SP can subscribe the tenant to a hardware plan. The tenant can be subscribed to different hardware plans that utilize resources on different SP virtualization hosts.

For tenants, hardware plans appear as cloud hosts on which tenants can create VM replicas. As soon as the tenant connects to the SP, Veeam Backup & Replication retrieves information about all hardware plans to which the SP subscribed this tenant and displays a list of cloud hosts that become available in the tenant backup infrastructure.

You can configure hardware plans on the following virtualization platforms:

* VMware host or cluster
* Hyper-V host or cluster

In This Section

* [Adding Hardware Plans](hardware_plans_add.md)
* [Managing Hardware Plans](managing_hardware_plans.md)

Page updated 10/3/2023

Page content applies to build 13.0.1.1071
