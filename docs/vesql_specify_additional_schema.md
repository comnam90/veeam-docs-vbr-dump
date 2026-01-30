---
title: "Step 8. Specify Additional Restore Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_specify_additional_schema.html"
last_updated: "8/24/2025"
product_version: "13.0.1.1071"
---

# Step 8. Specify Additional Restore Options


At this step of the wizard, specify additional restore options and click Restore.

* In the Filegroups section, select how filegroups should be restored for selected schema objects:

* Preserve filegroup if applicable — to preserve the file group state.
* Use the following filegroup — to select a file group on a target SQL Server instance.

For more information on filegroups, see [Microsoft Docs](https://learn.microsoft.com/en-us/sql/relational-databases/databases/database-files-and-filegroups?view=sql-server-ver16#filegroups).

* In the Partitioned tables section, select how partitioned tables should be restored:

* Preserve partition schema if applicable — to restore tables to the original partition schema.
* Use the following partition schema — to select a partition schema on a target SQL Server instance.
* Use the following filegroup — to select a file group on a target SQL Server instance.

[![Specifying Additional Restore Options](images/vesql_restore_schema_options.webp)](images/vesql_restore_schema_options.webp "Specifying Additional Restore Options")


