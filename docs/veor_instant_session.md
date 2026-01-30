---
title: "Managing Instant Recovery Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_instant_session.html"
last_updated: "8/19/2025"
product_version: "13.0.1.1071"
---

# Managing Instant Recovery Session


After you finish steps of the Instant Recovery wizard, Veeam Explorer for Oracle starts an instant recovery session which shows the progress of the recovery process.

Depending on the option you choose in the Instant Recovery wizard, switchover starts in one of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually

If you have selected the Manual switchover option, you must perform switchover manually as described in [Starting Switchover Manually](veor_manual_switchover.md).

|  |
| --- |
| Note |
| The instant recovery session closes automatically after switchover. |

Also, in the Instant Recovery session view, you can do the following:

* [Edit switchover settings](veor_instant_edit_settings.md).
* [Retry instant recovery](veor_retry.md) (in case instant recovery session fails for any reason).
* [Cancel instant recovery](veor_instant_cancel.md).

[![Viewing Instant Recovery Session](images/instant_recovery_session_veor.webp)](images/instant_recovery_session_veor.webp "Viewing Instant Recovery Session")


