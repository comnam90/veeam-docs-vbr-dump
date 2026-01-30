---
title: "Data Publishing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_data_publishing.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Data Publishing


Publishing an Oracle database allows you to temporarily attach the databases to the target Oracle server without launching restore. Publishing typically occurs faster than using standard restore features and could be convenient when, for example, your time to perform disaster-recovery operations is limited.

Veeam Explorer for Oracle mounts disks from the backup repository to the target machine (under the C:\VeeamFLR directory for Windows machines or the /run/media directory for Linux machines), retrieves required database files and attaches the associated database directly to Oracle Database so that you can perform required operations using Oracle Database tools such as Oracle SQL Developer.

After you have launched a publishing operation to an Oracle machine, you can quickly republish the latest or point-in-time state of the database to the same machine.

Once you are done working with the published database, you can export the modified database as an Oracle RMAN backup. For more information, see [Exporting as RMAN Backup](veor_export_as_rman.md).

Before publishing data, read the [Considerations and Limitations](veor_considerations.md) section.

In This Section

* [How Publishing Works](veor_how_publishing_works.md)
* [Publishing to Specified Server](veor_ptsr.md)
* [Publishing Latest or Point-in-Time State](veor_pit.md)
* [Exporting as RMAN backup](veor_export_as_rman.md)
* [Unpublishing Databases](veor_unpublishing.md)
* [Refreshing Database Status](veor_publishing_refresh.md)


