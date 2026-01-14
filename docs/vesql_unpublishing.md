---
title: "Unpublishing Databases"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_unpublishing.html"
last_updated: "8/24/2025"
product_version: "13.0.1.1071"
---

# Unpublishing Databases

In this article

Once you have finished working with published SQL databases, you may want to unpublish (detach) these databases from the target SQL server.

Detachment occurs in the following manner:

* Upon closing the Veeam Explorer for Microsoft SQL Server console, all published databases will be detached from the target SQL server automatically. Mount points will be also dismounted from under the C:\VeeamFLR directory.

* On manual unpublishing, databases will be detached at once but the restore point will remain mounted on the target machine for the next 15 minutes.

To unpublish a database manually, do the following:

1. In the navigation pane, under the Published databases node, select a published database.
2. On the Publish tab, select Unpublish Database.

Alternatively, in the navigation pane, right-click a published database and select Unpublish database.

To detach more than one published database simultaneously, right-click the root Published databases node and select Unpublish databases or select the root Published databases node and click Unpublish Databases on the Publish tab.

[![Unpublishing Databases](images/unpublish.webp)](images/unpublish.webp "Unpublishing Databases")

Page updated 8/24/2025

Page content applies to build 13.0.1.1071
