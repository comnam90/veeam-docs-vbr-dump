---
title: "cloud_connect_backup_getting_started"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_backup_getting_started.html"
last_updated: "6/20/2024"
product_version: "13.0.1.1071"
---


In this article

To provide Backup as a Service to tenants, the SP must set up the Veeam Cloud Connect Backup infrastructure.

As part of the configuration process, the SP must perform the following tasks:

1. [Deploy the SP Veeam backup server](cloud_connect_sp_vbr_deploy.md).
2. [Set up TLS certificates](cloud_connect_manage_ssl.md).
3. [Create cloud gateways](cloud_connect_gateways.md).
4. [Configure cloud repositories](cloud_connect_configure_repository.md).
5. [Optional] [Configure target WAN accelerators](cloud_connect_configure_wan.md).
6. [Create tenant accounts](cloud_connect_tenant.md).
7. [Communicate information about the tenant account and gateway to all tenants who plan to connect to the SP](cloud_connect_user_next.md).

Once the SP has configured necessary components, tenants can add the SP to their Veeam Backup & Replication consoles and use cloud repositories allocated to them in the SP Veeam Cloud Connect infrastructure.

Related Topics

* [Veeam Cloud Connect Backup](cloud_backup.md)
* [Veeam Cloud Connect Infrastructure](cloud_infrastructure.md)

Page updated 6/20/2024

Page content applies to build 13.0.1.1071
