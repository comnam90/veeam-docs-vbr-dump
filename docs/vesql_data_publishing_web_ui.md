---
title: "Data Publishing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_data_publishing_web_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Data Publishing


Publishing a Microsoft SQL Server database allows you to temporarily attach the database to the target Microsoft SQL Server machine without launching restore. Publishing typically occurs faster than using standard restore features and could be convenient when, for example, your time to perform disaster-recovery operations is limited.

Veeam Explorer for Microsoft SQL Server mounts disks from the backup repository to the target machine (under the C:\VeeamFLR directory), retrieves required database files and attaches the associated database directly to your Microsoft SQL Server instance so that you can perform required operations using SQL Server tools such as Microsoft SQL Server Management Studio.

Once you are done working with the published database, you can export the modified database as a BAK file. For more information, see [Exporting as BAK](vesql_publish_web_ui_export.md).

Before publishing data, read the [Considerations and Limitations](vesql_considerations.md) section.

In This Section

* [How Publishing Works](vesql_how_publishing_works_web_ui.md)
* [Publishing to Specified Server](vesql_publish_web_ui_tas.md)
* [Viewing Export Session](vesql_export_web_ui_manage_properties.md)

Page updated 2026-07-10

