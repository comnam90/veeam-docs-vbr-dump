---
title: "Failback Undo"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failback_undo.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Failback Undo


Failback undo is one of the ways to finalize failback. You can use this option if the vApp to which you failed back (the production vApp) works in a wrong way and you want to get back to the replica.

The failback undo operation is performed in the following way:

1. Veeam Backup & Replication powers off the production vApp.
2. Veeam Backup & Replication reverts the replica to its pre-failback state.
3. Veeam Backup & Replication powers on the replica and changes the replica state from Failback or Ready to Switch to Failover.

In This Section

* [Undoing Failback](vcd_failback_undoing.md)
* [Performing Failback Undo Retry](vcd_failback_undo_retry.md)


