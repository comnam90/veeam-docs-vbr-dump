---
title: "Configuring Source WAN Accelerators"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user_wan.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Configuring Source WAN Accelerators


To optimize VM traffic going to the Veeam Cloud Connect infrastructure during the backup copy and replication jobs, the SP and tenants can configure WAN accelerators on their sides.

WAN accelerators in the Veeam Cloud Connect infrastructure must be configured in the following way:

* The source WAN accelerator is configured on the tenant side. Every tenant who plans to work with the cloud repository and cloud hosts using WAN accelerators must configure at least one WAN accelerator on their side.
* The target WAN accelerator is configured on the SP side.

When the SP creates a tenant account, the SP can define if the tenant should be able to utilize a WAN accelerator deployed on the SP side. As soon as you connect to the SP, Veeam Backup & Replication retrieves the following information to identify if cloud resources available to you can or cannot use WAN acceleration:

* Information about all quotas on cloud repositories assigned to you by the SP
* Information about all cloud hosts provided to you by the SP through hardware plans

If the cloud repository and cloud host can use WAN acceleration, you can configure a source WAN accelerator on your side and create backup copy and replication jobs that will work using WAN accelerators.

![Configuring Source WAN Accelerators](images/cloud_replica_job_data_transfer.webp)

The configuration process for WAN accelerators in the Veeam Cloud Connect infrastructure is the same as the configuration process in a regular Veeam backup infrastructure. To learn more, see the [Adding WAN Accelerators](https://helpcenter.veeam.com/docs/vbr/userguide/wan_add.html?ver=13) section in Veeam Backup & Replication User Guide.

Related Concepts

[WAN Accelerators](cloud_connect_wan.md)


