---
title: "Editing Instant Recovery Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_ir_web_ui_manage_edit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Instant Recovery Settings


If you have started an instant recovery session and want to change switchover settings, you can edit the instant recovery settings.

To change the switchover settings of an instant recovery session, do the following:

1. In the Database recovery sessions view, select an instant recovery session.
2. Click Edit.

Alternatively, you can right-click the session and select Edit.

[![Editing Instant Recovery Settings](images/vesql_ir_web_ui_manage_edit_edit.webp)](images/vesql_ir_web_ui_manage_edit_edit.webp "Editing Instant Recovery Settings")

1. In the Instant Recovery wizard, change the switchover type at the Switchover step.

Under Switchover type, select one of the following options:

* Auto: switchover is performed automatically with minimal possible downtime once the database is ready.
* Manual: switchover can be performed manually at any time after the database is ready.

* Scheduled at: switchover is performed at the specified date and time. Use the calendar to specify the date and time.

[![Specifying Database Switchover Scheduling Options](images/vesql_ir_web_ui_manage_edit_switchover_scheduling.webp)](images/vesql_ir_web_ui_manage_edit_switchover_scheduling.webp "Specifying Database Switchover Scheduling Options")

1. At the Summary step, review the switchover settings. To copy the summary to the clipboard, click Copy to Clipboard. To save the switchover settings, click Finish.

[![Reviewing Instant Recovery Summary](images/vesql_ir_web_ui_manage_edit_summary.webp)](images/vesql_ir_web_ui_manage_edit_summary.webp "Reviewing Instant Recovery Summary")

Page updated 2026-07-10

