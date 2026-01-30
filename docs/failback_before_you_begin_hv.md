---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/failback_before_you_begin_hv.html"
last_updated: "1/29/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you perform failback, check the following prerequisites:

* VMs for which you plan to perform failback must be successfully replicated at least once.
* VM replicas must be in the Failover state.
* The target host version must be equal or later than the source host version. However, you can fail back from the source 2016 host to the target 2012 R2 host if a VM replica configuration is lower than 8.0.
* The target VM configuration version must be equal or higher than the source VM configuration version.
* On non-Microsoft Windows SMB3 storage, for example, Tintri, Veeam Backup & Replication may display the "Failed to disable integrity bit on disk N" warning during VM restore. You can ignore this warning for non-Microsoft Windows SMB3 storage.


