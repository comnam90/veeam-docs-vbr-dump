---
title: "Canceling Instant Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_instant_cancel.html"
last_updated: "8/24/2025"
product_version: "13.0.1.1071"
---

# Canceling Instant Recovery


If you have finished working with the published database and you do not want to switch over to it, you can cancel the instant recovery session.

You can do this by canceling instant recovery in either Veeam Explorer for Microsoft SQL Server or the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| Consider the following:   * Closing either the Veeam Explorer for Microsoft SQL Server window or the Veeam Backup & Replication console does not cancel the instant recovery session. * You do not need to cancel the instant recovery session if switchover is already performed. The session closes automatically after switchover. |

Canceling Instant Recovery in Veeam Explorer for Microsoft SQL Server

To cancel the instant recovery session in Veeam Explorer for Microsoft SQL Server, do the following:

1. In the navigation pane, under the Instant Recovery node, select a published database.
2. On the Instant Recovery tab, select Cancel.

Alternatively, you can right-click the database and select Cancel.

[![Cancelling Instant Recovery](images/instant_cancel.webp)](images/instant_cancel.webp "Cancelling Instant Recovery")

Canceling Instant Recovery in Veeam Backup & Replication Console

To cancel the instant recovery session in the Veeam Backup & Replication console, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the navigation pane, select Instant Database Recovery.
3. In the preview pane, select the session and in the Instant Database Recovery tab click Stop Publishing.

Alternatively, you can right-click the session and click Stop publishing.

[![Stopping Publishing](images/vesql_instant_stop_publishing.webp)](images/vesql_instant_stop_publishing.webp "Stopping Publishing")


