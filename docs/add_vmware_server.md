---
title: "Adding VMware vSphere Servers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/add_vmware_server.html"
last_updated: "9/29/2025"
product_version: "13.0.1.1071"
---

# Adding VMware vSphere Servers

In this article

You must add to the backup infrastructure VMware vSphere servers that you plan to use as source and target for backup, replication and other activities.

You can add vCenter Servers and ESXi hosts. If an ESXi host is managed by a vCenter Server, it is recommended that you add the vCenter Server, not a standalone ESXi host. If you move VMs between ESXi hosts managed by the vCenter Server, you will not have to re-configure jobs in Veeam Backup & Replication. Veeam Backup & Replication will automatically locate migrated VMs and continue processing them as usual. Connecting a vCenter Server instead of standalone ESXi hosts provides more flexibility at work.

Related Topics

* [Adding VMware vSphere Server Using Console](add_vmware_server_console.md)
* [Adding VMware vSphere Server Using Web UI](add_vmware_server_web.md)

Page updated 9/29/2025

Page content applies to build 13.0.1.1071
