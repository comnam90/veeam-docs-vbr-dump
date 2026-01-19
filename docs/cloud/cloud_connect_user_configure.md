---
title: "Setting Up Tenant Veeam Cloud Connect Infrastructure"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user_configure.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Setting Up Tenant Veeam Cloud Connect Infrastructure


To be able to use cloud repository and cloud replication resources, you must set up Veeam Cloud Connect infrastructure components on the tenant side.

As part of the configuration process, you must perform the following tasks:

1. [Deploy the tenant Veeam backup server](cloud_connect_user_vbr_deploy.md).
2. [Connect source virtualization hosts](cloud_connect_hypervisor_add.md).
3. [Find a service provider](cloud_connect_sp_find.md).
4. [Connect to a service provider](cloud_connect_sp.md).
5. [For Veeam Cloud Connect Replication] [Specify default gateways](cloud_connect_default_gateways.md).
6. [Optional] [Configure source WAN accelerator](cloud_connect_configure_wan.md).

Once you have performed these tasks, you can configure data protection jobs in Veeam Backup & Replication and target them at the cloud repository or cloud host.

Related Concepts

[Veeam Cloud Connect Infrastructure](cloud_infrastructure.md)


