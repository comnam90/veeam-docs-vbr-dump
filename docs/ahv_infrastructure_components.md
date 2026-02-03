---
title: "Solution Architecture"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_infrastructure_components.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# Solution Architecture


Starting from version 6.0, Veeam Plug-in for Nutanix AHV supports 2 deployment scenarios:

* [Prism Central deployment scenario](ahv_infrastructure_prism_central.md) allows you to protect workloads that reside in multiple clusters registered with a Prism Central.

This scenario provides a centralized web console that allows you to manage backup and restore operations performed for workloads in all the registered clusters. Therefore, it reduces time required to install, configure and maintain Veeam Plug-in for Nutanix AHV,

* [Standalone cluster deployment scenario](ahv_infrastructure_cluster.md) allows you to protect workloads that reside in a specific cluster.

Even if you add multiple clusters to the backup infrastructure, Veeam Plug-in for Nutanix AHV will treat each cluster as a dedicated virtual environment. Therefore, backup and restore operations performed for workloads in each cluster will be managed separately.

You can also combine these scenarios to support your own data protection strategy. However, keep in mind that you cannot add to the backup infrastructure both a Prism Central and a standalone Nutanix AHV cluster that is registered with this Prism Central.


