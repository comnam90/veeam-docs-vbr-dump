---
title: "Before You Begin"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_failover_plan_byb.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

Before you create a cloud failover plan, check the following prerequisites and limitations:

* VMs that you plan to include in the failover plan must be successfully replicated at least once.

* You cannot select to use pre-failover and post-failover scripts for the cloud failover plan. As tenant cloud failover plans and VM replicas are stored on the SP side, the responsibility to create and manage scripts lays on the SP. To use pre-failover and post-failover scripts, the SP must create those scripts in advance and select them in the cloud failover plan settings before you run the cloud failover plan. Veeam Backup & Replication supports script files in BAT and CMD formats and executable files in the EXE format.
* You cannot use the same cloud failover plan for full site failover of snapshot-based replicas and CDP replicas.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
