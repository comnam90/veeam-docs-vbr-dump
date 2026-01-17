---
title: "Creating Subtenant Account for Standalone Tenant"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_subtenant_create.html"
last_updated: "5/22/2024"
product_version: "13.0.1.1071"
---

# Creating Subtenant Account for Standalone Tenant


Typically, the procedure of subtenant accounts registration is performed by the tenant on the tenant Veeam backup server.

When you create a subtenant account, remember to save a user name and password for the created subtenant account. You must pass this data to the end user who will use the subtenant account. When configuring a Veeam Agent backup job targeted at the cloud repository, the user must enter the user name and password for the subtenant account to connect to the SP backup server.

Before creating subtenant accounts, [check prerequisites](subtenant_create_before.md). Then use the New Subtenant wizard to add a new subtenant account.

1. [Launch the New Subtenant wizard](subtenant_create_launch.md).
2. [Specify subtenant settings](subtenant_create_settings.md).
3. [Allocate subtenant quota](subtenant_create_quota.md).
4. [Finish working with the wizard](subtenant_create_finish.md).

Related Concepts

[Subtenants](cloud_connect_subtenants.md)


