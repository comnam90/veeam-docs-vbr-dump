---
title: "Failover Undo"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failover_undo.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Failover Undo


Failover undo is one of the ways to finalize failover. When you undo failover, you switch back from a vApp replica to the original vApp. Veeam Backup & Replication discards all changes made to the vApp replica while it was in the Failover state.

The failover undo operation is performed in the following way:

1. Veeam Backup & Replication reverts the replica to its pre-failover state. To do this, Veeam Backup & Replication powers off the vApp replica and gets it back to the latest restore point in the replication chain.
2. The state of the replica gets back to Ready, and Veeam Backup & Replication resumes replication activities for the original vApp on the source host.

In This Section

* [Undoing Failover](vcd_undoing_failover.md)
* [Performing Failover Undo Retry](vcd_undoing_failover_retry.md)


