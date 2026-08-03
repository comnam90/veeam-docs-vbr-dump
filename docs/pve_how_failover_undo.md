---
title: "Failover Undo"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_how_failover_undo.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Failover Undo


Failover undo is one of the ways to finalize failover. When you undo failover, you switch back from a VM replica to the original VM. Veeam Backup & Replication discards all changes made to the VM replica while it was in the Failover state.

The failover undo operation is performed in the following way:

1. Veeam Backup & Replication reverts the VM replica to its pre-failover state. To do this, Veeam Backup & Replication powers off the VM replica and gets it back to the state of the latest snapshot in the snapshot chain. Data from the snapshot file is used to discard the changes made while the VM replica was in the Failover state .
2. The state of the VM replica gets back to Ready, and Veeam Backup & Replication resumes replication activities for the original VM on the source host.

Related Topics

[Undoing Failover](pve_failover_undo.md)

Page updated 2026-07-29

