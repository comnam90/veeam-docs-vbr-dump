---
title: "Step 2. Specify Policy Name and Advanced Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_policy_name.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# Step 2. Specify Policy Name and Advanced Settings

In this article

At the Name step of the wizard, specify a name and description for the CDP policy, and choose whether you want to use replica seeding or network mapping:

1. In the Name field, enter a name for the CDP policy.
2. In the Description field, provide a description for future reference.
3. If a network between your production and disaster recovery (DR) sites has low bandwidth, and you want to reduce the amount of traffic sent during the initial synchronization of the CDP policy, select the Replica seeding (for low bandwidth DR sites) check box.

When selected, this check box enables the Seeding step where you will have to configure replica seeding and mapping.

1. If your DR site networks do not match your production site networks, select the Network remapping (for DR sites with different virtual networks) check box.

When selected, this check box enables the Network step where you will have to configure a network mapping table.

1. If the IP addressing scheme in your production site differs from the scheme in the DR site, select the Replica re-IP (for DR sites with different IP addressing scheme) check box.

When selected, this check box enables the Re-IP step where you will have to configure replica re-IP rules.

![Step 2. Specify Policy Name and Advanced Settings](images/cdp_policy_name.webp "Specify name")

Related Topics

[Replica Seeding and Mapping](cdp_seeding.md)

Page updated 8/20/2025

Page content applies to build 13.0.1.1071
