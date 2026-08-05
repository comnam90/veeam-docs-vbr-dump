---
title: "Step 6. Finalize Instant Recovery Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_ir_web_ui_multiple_pit_finalize_ir_session.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Finalize Instant Recovery Session


After you finish steps of the Instant Recovery wizard, Veeam Explorer for Microsoft SQL Server starts an instant recovery session.

In the Database recovery sessions view, you can see the progress of the recovery, edit switchover settings, cancel instant recovery, and start manual switchover (if you have selected the Manual switchover option in the Instant Recovery wizard).

Depending on the selected switchover option, switchover starts in one of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually

If you have selected the Manual switchover option, you must perform switchover manually as described in [Starting Switchover Manually](vesql_ir_web_ui_switchover_manual.md).

[![Finalizing Instant Recovery Session](images/instant_recovery_session_multiple_same_web_ui.webp)](images/instant_recovery_session_multiple_same_web_ui.webp "Finalizing Instant Recovery Session")

Related Topics

* [Managing Instant Recovery Session](vesql_ir_web_ui_manage.md)
* [Switchover](vesql_ir_web_ui_switchover.md)

Page updated 2026-07-07

