---
title: "Creating Subtenant Account for Standalone Tenant"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_subtenant_create_sp.html"
last_updated: "5/22/2024"
product_version: "13.0.1.1071"
---


In this article

The procedure of subtenant accounts registration can be performed by the SP on the SP Veeam backup server.

When you create a subtenant account for a standalone tenant account, remember to save a user name and password for the created subtenant account. You must pass this data to the subtenant. When configuring a backup job targeted at the cloud repository, the subtenant must enter the user name and password for the subtenant account to connect to the SP backup server.

To add a new subtenant account, use the New Subtenant wizard.

1. [Launch the New Subtenant wizard](subtenant_create_sp_launch.md).
2. [Specify subtenant settings](subtenant_create_sp_settings.md).
3. [Allocate subtenant quota](subtenant_create_sp_quota.md).
4. [Finish working with the wizard](subtenant_create_sp_finish.md).

Related Concepts

[Subtenants](cloud_connect_subtenants.md)

Page updated 5/22/2024

Page content applies to build 13.0.1.1071
