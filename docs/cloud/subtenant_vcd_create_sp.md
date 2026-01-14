---
title: "subtenant_vcd_create_sp"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/subtenant_vcd_create_sp.html"
last_updated: "5/22/2024"
product_version: "13.0.1.1071"
---


In this article

The procedure of subtenant accounts registration can be performed by the SP on the SP Veeam backup server.

After you create a subtenant account for a VMware Cloud Director tenant account, pass the user name of the created account to the subtenant. When configuring a backup job targeted at the cloud repository, the subtenant must enter the user name for the subtenant account to connect to the SP backup server.

Before creating subtenant accounts for a VMware Cloud Director tenant account, [check prerequisites](subtenant_vcd_create_sp_before.md). Then use the New Subtenant wizard to add a new subtenant account.

1. [Launch the New Subtenant wizard](subtenant_vcd_create_sp_launch.md).
2. [Select the Cloud Director user](subtenant_vcd_create_sp_settings.md).
3. [Allocate subtenant quota](subtenant_vcd_create_sp_quota.md).
4. [Finish working with the wizard](subtenant_vcd_create_sp_finish.md).

Related Concepts

* [Subtenants](cloud_connect_subtenants.md)
* [Subtenant Accounts for VMware Cloud Director Tenant Accounts](cloud_vcloud_director_tenant.md#vcd_subtenants)

Page updated 5/22/2024

Page content applies to build 13.0.1.1071
