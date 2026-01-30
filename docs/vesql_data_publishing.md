---
title: "Data Publishing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_data_publishing.html"
last_updated: "3/28/2024"
product_version: "13.0.1.1071"
---

# Data Publishing


Publishing a Microsoft SQL Server database allows you to temporarily attach the database to the target Microsoft SQL Server without launching restore. Publishing typically occurs faster than using standard restore features and could be convenient when, for example, your time to perform disaster-recovery operations is limited.

Veeam Explorer for Microsoft SQL Server mounts disks from the backup repository to the target machine (under the C:\VeeamFLR directory), retrieves required database files and attaches the associated database directly to your Microsoft SQL Server instance so that you can perform required operations using SQL Server tools such as Microsoft SQL Server Management Studio.

After you have launched a publishing operation to a Microsoft SQL Server machine, you can quickly republish the latest or point-in-time state of the database to the same machine.

Once you are done working with the published database, you can export the modified database as a BAK file. For more information, see [Exporting as BAK](vesql_published_export.md).

Before publishing data, read the [Considerations and Limitations](vesql_considerations.md) section.

In This Section

* [How Publishing Works](vesql_how_publishing_works.md)
* [Publishing to Specified Server](vesql_publishing_databases.md)
* [Publishing Latest or Point-in-Time State](vesql_publishing_latest_or_pit.md)
* [Exporting as BAK](vesql_published_export.md)
* [Unpublishing Databases](vesql_unpublishing.md)
* [Refreshing Database Status](vesql_refreshing_published_database.md)


