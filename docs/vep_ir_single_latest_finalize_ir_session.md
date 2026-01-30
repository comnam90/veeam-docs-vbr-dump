---
title: "Step 3. Finalize Instant Recovery Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_ir_single_latest_finalize_ir_session.html"
last_updated: "11/7/2023"
product_version: "13.0.1.1071"
---

# Step 3. Finalize Instant Recovery Session


After you finish steps of the Instant Recovery wizard, Veeam Explorer for PostgreSQL starts an instant recovery session.

In the Instant Recovery session view, you can see the progress of the recovery, edit switchover settings, retry instant recovery and cancel instant recovery. For more information, see [Managing Instant Recovery Session](vep_ir_managing_session.md).

Depending on the selected switchover option, switchover starts in one of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually, anytime after synchronization

If you have selected the Manual switchover option, you must perform switchover manually as described in [Starting Switchover Manually](vep_ir_switchover_manual.md).

If switchover is successfully performed or the instant recovery session is canceled, the instance moves from the Instant Recovery node to the Completed node at the bottom of the navigation pane.

[![Finalizing Instant Recovery Session](images/vep_ir_finalize.webp)](images/vep_ir_finalize.webp "Finalizing Instant Recovery Session")

Related Topics

* [Managing Instant Recovery Session](vep_ir_managing_session.md)
* [Switchover](vep_ir_switchover.md)


