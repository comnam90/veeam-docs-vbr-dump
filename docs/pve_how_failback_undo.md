---
title: "Failback Undo"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_how_failback_undo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Failback Undo


Failback undo is one of the ways to finalize failback. When you undo failback, you confirm that the VM to which you failed back (the production VM) and changes sent to it during failback work in a wrong way and you want to get back to the replica.

The failback undo operation is performed in the following way:

1. Veeam Backup & Replication powers off the production VM.
2. Veeam Backup & Replication reverts the VM replica to its pre-failback state.
3. Veeam Backup & Replication powers on the VM replica and changes the VM replica state from Failback to Failover.

Related Topics

[Perfroming Failback](pve_failback_perform_finish.md)

Page updated 2026-07-29

