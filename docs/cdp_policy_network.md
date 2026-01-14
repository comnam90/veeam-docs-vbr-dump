---
title: "Step 7. Configure Network Mapping"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_policy_network.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# Step 7. Configure Network Mapping

In this article

The Network step of the wizard is available if you have selected the Network remapping option at the Name step of the wizard.

At the Network step of the wizard, configure a network mapping table. This table maps networks in the production site to networks in the disaster recovery (DR) site. When the replication session starts, Veeam Backup & Replication will check the network mapping table. Then Veeam Backup & Replication will update replica configuration to replace the production networks with the specified networks in the DR site. As a result, you will not have to re-configure network settings manually.

To add a row to the network mapping table:

1. Click Add.
2. In the Network Mapping window, click Browse next to the Source network field.
3. In the Select Network window, select the production network to which the source workloads are connected and click OK.
4. In the Network Mapping window, click Browse next to the Target network field.
5. In the Select Network window, select a network in the DR site to which replicas will be connected and click OK.
6. In the Network Mapping window, click OK.

![Step 7. Configure Network Mapping](images/cdp_policy_network.webp "Specify network mapping")

Page updated 8/20/2025

Page content applies to build 13.0.1.1071
