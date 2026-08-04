---
title: "Exporting as BAK"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_publish_web_ui_export.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Exporting as BAK


To save the changes you make while working with your published database, use the export feature. It exports the modified database as BAK, preserving all changes made during the publishing session.

To launch the Export Backup wizard, do the following:

1. In the Database recovery sessions view, select a publishing session.
2. Click Export Backup.

Alternatively, you can right-click the publishing session and select Export Backup.

[![Exporting as BAK](images/vesql_publish_web_ui_export_wizard.webp)](images/vesql_publish_web_ui_export_wizard.webp "Exporting as BAK")

In the Export Backup wizard, perform the following steps:

1. At the Target Machine step, specify the DNS name or IP address of the target Windows server and the credentials of an account that can access it.

[![Specifying the Target Machine](images/vesql_publish_web_ui_export_target_server.webp)](images/vesql_publish_web_ui_export_target_server.webp "Specifying the Target Machine")

1. At the Target Path step, specify the path to the export file. To reduce the output file size, select the Enable compression check box.

|  |
| --- |
| Note |
| Consider the following:   * Make sure the account you use has at least Read and Write permissions on the target directory. * Compression is unavailable if the staging SQL server runs any Express Edition of Microsoft SQL Server. |

[![Specifying Database Export Location](images/vesql_publish_web_ui_export_location.webp)](images/vesql_publish_web_ui_export_location.webp "Specifying Database Export Location")

1. At the Summary step, review the export settings and click Finish. To copy the summary to the clipboard, click Copy to Clipboard.

After you finish the steps of the Export Backup wizard, Veeam Explorer for Microsoft SQL Server starts an export session. For information on how to track this session, see [Viewing Export Session](vesql_export_web_ui_manage_properties.md).[![Reviewing Export Settings](images/vesql_publish_web_ui_export_summary.webp)](images/vesql_publish_web_ui_export_summary.webp "Reviewing Export Settings")

Page updated 2026-07-10

