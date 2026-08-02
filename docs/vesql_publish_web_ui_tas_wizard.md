---
title: "Step 1. Launch Publish Database Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_publish_web_ui_tas_wizard.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 1. Launch Publish Database Wizard


To launch the Publish Database wizard, open the Browse tab and do the following:

1. In the navigation pane, select a database.
2. In the upper part of the preview pane, select Publish to Another Server.

Alternatively, you can open the Browse tab, right-click a database and select Publish to Another Server.

[![Launching Publish Database Wizard](images/vesql_publish_web_ui_tas_wizard_wizard.webp)](images/vesql_publish_web_ui_tas_wizard_wizard.webp "Launching Publish Database Wizard")

After you complete the wizard steps, a new Published databases node appears at the top of the navigation pane. Under this node, you can find the databases that have been published during the current session of Veeam Explorer for Microsoft SQL Server.

[![Finding Published Database](images/vesql_publish_web_ui_tas_wizard_find.webp)](images/vesql_publish_web_ui_tas_wizard_find.webp "Finding Published Database")

To work with published databases, open a SQL tool you prefer, for example, Microsoft SQL Server Management Studio and locate your published databases.

The figure below demonstrates a published database (db1\_published) available in the Object Explorer window of your Microsoft SQL Server Management Studio console. This database is also being referenced in the Veeam Backup & Replication web UI, under the DB Recovery node.

![Step 1. Launch Publish Database Wizard](images/vesql_publish_web_ui_tas_wizard_object_explorer.webp "Published Database in Object Explorer")

Page updated 2026-07-08

