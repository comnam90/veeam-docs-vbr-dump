---
title: "Finalizing Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_failover_finalize.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Finalizing Failover


Veeam Backup & Replication provides you with a number of options to finalize failover to VM replicas:

* [Perform permanent failover](pve_failover_permanent.md) — permanently switch from the original VM to a VM replica and use this replica as the original VM.
* [Perform failback](pve_failback_perform.md) — shift all processes back to the original VM and send to the original VM all changes that took place while the VM replica was running.

|  |
| --- |
| Tip |
| You can also shift all processes back to the original VM and discard all changes made to the VM replica while it was running. To do that, perform the undo failover operation as described in section [Undoing Failover](pve_failover_undo.md). |

Related Topics

* [Permanent Failover](pve_how_permanent_failover.md)
* [Failback](pve_how_failback.md)
* [Failover Undo](pve_how_failover_undo.md)

Page updated 2026-07-16

