---
title: "cloud_cdp_failover_and_failback"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_cdp_failover_and_failback.html"
last_updated: "11/9/2023"
product_version: "13.0.1.1071"
---


In this article

In case of software or hardware malfunction on the production site, a tenant can quickly recover a corrupted VM by failing over to its CDP replica in the cloud. When you perform cloud failover, a replicated VM on the cloud host takes over the role of the original VM. A tenant can fail over to the latest state of a replica or to any of its good known restore points.

For CDP replicas, Veeam Cloud Connect offers the same failover scenarios as for regular, snapshot-based replicas:

* Full site failover — the whole production site becomes unavailable and all critical VMs that run interdependent applications fail over to their replicas on the cloud host.
* Partial site failover — one or several VMs become corrupted and fail over to their replicas on the cloud host.

To learn more, see [Cloud Replica Failover and Failback](cloud_failover_and_failback.md).

Related Tasks

* [Performing Full Site Failover](performing_full_site_failover.md)
* [Performing Partial Site Failover](performing_partial_site_failover.md)
* [Performing Failback](performing_failback_to_production.md)
* [Managing Tenant Cloud Failover Plans](cloud_failover_plan_manage_sp.md)

Page updated 11/9/2023

Page content applies to build 13.0.1.1071
