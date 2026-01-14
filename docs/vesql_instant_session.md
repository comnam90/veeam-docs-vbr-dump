---
title: "Managing Instant Recovery Session"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_instant_session.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Managing Instant Recovery Session

In this article

After you finish steps of the Instant Recovery wizard, Veeam Explorer for Microsoft SQL Server starts an instant recovery session which shows the progress of the recovery process.

Depending on the option you choose in the Instant Recovery wizard, switchover starts in one of the following ways:

* Automatically, immediately after synchronization
* Automatically, according to a specified schedule
* Manually

If you have selected the Manual switchover option, you must perform switchover manually as described in [Starting Switchover Manually](vesql_manual_switchover.md).

|  |
| --- |
| Note |
| The instant recovery session closes automatically after switchover. |

Also, in the Instant Recovery session view, you can do the following:

* [Edit switchover settings](vesql_instant_edit_settings.md).
* [Retry instant recovery](vesql_retry.md) (in case instant recovery session fails for any reason).
* [Cancel instant recovery](vesql_instant_cancel.md).

[![Managing Instant Recovery Session](images/instant_recovery_session_switch.webp)](images/instant_recovery_session_switch.webp "Managing Instant Recovery Session")

Page updated 8/25/2025

Page content applies to build 13.0.1.1071
