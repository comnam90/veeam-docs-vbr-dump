---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_failover_byb.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you fail over to a replica, check the following prerequisites:

* [For Linux-based backup server] Add the default Microsoft Windows mount server. For more information, see [Mount Servers](mount_server.md).
* You can perform failover for workloads that have been successfully replicated at least once.
* If you plan to fail over virtual machines with more than 120 disks in total, [create a failover plan](uni_cdp_failover_plan.md) for these virtual machines. Do not launch the failover process manually.
* Replicas must be in the Ready state.
* Host vMotion is not allowed during failover.


