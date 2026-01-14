---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_policy_byb.html"
last_updated: "8/2/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a CDP policy, check the following prerequisites:

* Check that all the required components are added to the backup infrastructure. For more information on the required components, see [Backup Infrastructure for CDP](cdp_infrastructure.md).
* The I/O filter must be installed on each cluster where VMs that you plan to protect reside. For more information on how to install the filter, see [Installing I/O Filter](cdp_io_filter_install.md).
* If you plan to use [replica seeding](cdp_seeding.md), you must create a seed as described in section [Creating Replica Seeds for CDP](creating_replica_seed.md).

* If you plan to protect VMware Cloud Director objects, consider using the dedicated policy. For more information, see [CDP for VMware Cloud Director](vcloud_director_cdp.md).

Page updated 8/2/2024

Page content applies to build 13.0.1.1071
