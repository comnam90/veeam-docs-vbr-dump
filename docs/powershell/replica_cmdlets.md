---
title: "Failover and Failback"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/replica_cmdlets.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Failover and Failback


When you have a replica of a VM, you can use it to fail over to it in case of the original VM malfunction or for testing.

In This Section

| VMware | Hyper-V | Operation |
| --- | --- | --- |
| [Start-VBRViReplicaFailover](start-vbrvireplicafailover.md) | [Start-VBRHvReplicaFailover](start-vbrhvreplicafailover.md) | Fail over corrupted VMs to their replicas. |
| [Start-VBRViReplicaFailback](start-vbrvireplicafailback.md) | [Start-VBRHvReplicaFailback](start-vbrhvreplicafailback.md) | Fails back to production host. |
| [Stop-VBRViReplicaFailback](stop-vbrvireplicafailback.md) | [Stop-VBRHvReplicaFailback](stop-vbrhvreplicafailback.md) | Undoes replica failback. |
| [Stop-VBRReplicaFailover](stop-vbrreplicafailover.md) |  | Undoes replica failover. |


