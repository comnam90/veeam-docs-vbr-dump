---
title: "Failover Plans"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_failover_plan.html"
last_updated: "10/28/2025"
product_version: "13.0.1.1071"
---

# Failover Plans

In this article

A failover plan helps you perform failover for dependent workloads one by one, as a group. To do this automatically, you can prepare a failover plan.

In the failover plan, you define the order in which workloads must be processed and an interval of time for which Veeam Backup & Replication must wait before starting the failover operation for the next workload in the list. The failover plan helps ensure that some workloads, such as a DNS server, are already running at the time the dependent workloads start.

|  |
| --- |
| Important |
| The failover plan must be created in advance. |

In case the primary workload group goes offline, you can start the failover plan manually. When you start the plan, you can choose to fail over to the latest state or select the point in time to which replicas must be started. Veeam Backup & Replication will look for the closest restore points to this point in time and use them to start replicas.

The failover process is performed in the following way:

1. For each workload, Veeam Backup & Replication detects its replica. The workloads whose replicas are already in the Failover or Failback state are skipped from processing.
2. The replicas are started in the order they appear in the failover plan within the set time intervals.

Page updated 10/28/2025

Page content applies to build 13.0.1.1071
