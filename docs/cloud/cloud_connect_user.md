---
title: "Configuring Standalone Tenant Account"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user.html"
last_updated: "6/19/2024"
product_version: "13.0.1.1071"
---


In this article

To let a tenant work with Veeam Cloud Connect backup and replication resources, you must register a tenant account on the SP Veeam backup server. Tenants with registered tenant accounts have access to cloud repositories and cloud hosts. Tenants without accounts cannot connect to the SP and use Veeam Cloud Connect resources.

Before creating a tenant account, [check prerequisites](cloud_connect_user_before.md). Then use the New Tenant wizard to register a new tenant account.

1. [Launch the New Tenant wizard](cloud_connect_user_launch.md).
2. [Specify tenant settings](cloud_connect_user_settings.md).
3. [Specify bandwidth settings](cloud_connect_user_throttling.md).
4. [Allocate backup repository resources](cloud_connect_user_resources.md).
5. [Allocate compute resources for tenant VM replicas](cloud_connect_user_compute_resources.md).
6. [Specify network settings for failover](cloud_connect_user_network_failover.md).
7. [Assess results](cloud_connect_user_assess_results.md).
8. [Finish working with the wizard](cloud_connect_user_finish.md).
9. [What you do next](cloud_connect_user_next.md).

Related Concepts

* [SP and Tenant Roles](cloud_roles.md)
* [Tenant Lease and Quota](lease_and_quota.md)

Page updated 6/19/2024

Page content applies to build 13.0.1.1071
