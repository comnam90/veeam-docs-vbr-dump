---
title: "Managing Instant Recovery Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_ir_managing_session.html"
last_updated: "2/21/2025"
product_version: "13.0.1.1071"
---

# Managing Instant Recovery Session


After you finish the steps of the Instant Recovery wizard, Veeam Explorer for PostgreSQL starts an instant recovery session which shows the progress of the recovery process.

Depending on the option you choose in the Instant Recovery wizard, switchover starts in one of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually

If you have selected the Manual switchover option, you must perform switchover manually as described in [Starting Switchover Manually](vep_ir_switchover_manual.md).

|  |
| --- |
| Note |
| The instant recovery session closes automatically after switchover. |

Also, in the Instant Recovery session view, you can do the following:

* [Edit switchover settings](vep_ir_edit_settings.md).
* [Retry instant recovery](vep_ir_retry.md) (in case instant recovery session fails for any reason).
* [Cancel instant recovery](vep_ir_cancel.md).

[![Managing Instant Recovery Session](images/vep_ir_finalize.webp)](images/vep_ir_finalize.webp "Managing Instant Recovery Session")


