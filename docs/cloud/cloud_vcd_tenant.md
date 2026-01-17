---
title: "Configuring VMware Cloud Director Tenant Account"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_vcd_tenant.html"
last_updated: "2/8/2024"
product_version: "13.0.1.1071"
---

# Configuring VMware Cloud Director Tenant Account


To let a tenant work with a cloud host that utilizes VMware Cloud Director resources, you must register a VMware Cloud Director tenant account on the SP Veeam backup server. Tenants with registered VMware Cloud Director accounts have access to organization VDCs exposed as cloud hosts for tenant VM replicas. Tenants without VMware Cloud Director accounts cannot create VM replicas on cloud hosts that utilize VMware Cloud Director resources of the SP.

Before creating a VMware Cloud Director tenant account, [check prerequisites](cloud_vcd_tenant_before.md). Then use the New Tenant wizard to register a new VMware Cloud Director tenant account.

1. [Launch the New Tenant wizard](cloud_vcd_tenant_launch.md).
2. [Specify bandwidth settings](cloud_vcd_tenant_throttling.md).
3. [Allocate backup repository resources](cloud_vcd_tenant_backup.md).
4. [Allocate compute resources for tenant VM replicas](cloud_vcd_tenant_replication.md).
5. [Specify network settings for failover](cloud_vcd_tenant_network.md).
6. [Assess results](cloud_vcd_tenant_apply.md).
7. [Finish working with the wizard](cloud_vcd_tenant_finish.md).
8. [What you do next](cloud_vcd_tenant_next.md).

Related Concepts

[VMware Cloud Director Support](cloud_vcloud_director.md)


