---
title: "Support for Capacity Tier"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_capacity_tier.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

SPs who use a scale-out backup repository as a cloud repository can use the Capacity Tier functionality. This functionality allows the SP to offload backup chains created by tenant jobs from an on-premises extent of a scale-out backup repository to a cloud-based object storage. For more information, see the [Capacity Tier](https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier.html?ver=13) section in the Veeam Backup & Replication User Guide.

Veeam Backup & Replication supports offload to capacity tier for backups created by tenant VM backup jobs, Veeam Agent backup jobs and backup copy jobs.

For the tenant, backups in capacity tier are displayed in the Veeam backup console in the same way as regular cloud backups. The tenant is unaware of where their actual backup files reside — in performance tier or capacity tier — and cannot copy backup data between the capacity tier and performance tier. The tenant can perform the same data restore operations with backups in capacity tier as with backups in performance tier.

The SP can download tenant data that was offloaded to the capacity tier back to the performance tier. To learn more, see [Downloading Tenant Data from Capacity Tier](cc_capacity_tier_download.md).

Related Tasks

[Downloading Tenant Data from Capacity Tier](cc_capacity_tier_download.md)

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
