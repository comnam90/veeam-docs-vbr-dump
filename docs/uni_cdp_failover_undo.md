---
title: "Failover Undo"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_failover_undo.html"
last_updated: "10/15/2025"
product_version: "13.0.1.1071"
---

# Failover Undo


Failover undo is one of the ways to finalize failover. When you undo failover, you switch back from a replica to the source workload. Veeam Backup & Replication discards all changes made to the replica while it was in the Failover state.

The failover undo operation is performed in the following way:

1. Veeam Backup & Replication reverts the replica to its pre-failover state. To do this, Veeam Backup & Replication powers off the replica and gets it back to the latest restore point in the replication chain. Changes that were written to the protective virtual disks (<disk\_name>-interim.vmdk) while the replica was in the Failover state are discarded.
2. The state of the replica gets back to Ready, and Veeam Backup & Replication resumes replication activities for the source workload.


