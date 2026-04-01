---
title: "Retention of Microsoft SQL Server Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_retention_tools.html"
last_updated: "3/26/2026"
product_version: "13.0.1.2067"
---

# Retention of Microsoft SQL Server Backups


Veeam Plug-In for Microsoft SQL Server has the following retention tools to manage old and outdated backups:

* Retention policy. When applying the retention policy, Veeam Plug-In checks the backup chain and removes outdated restore points from the backup chain. The retention policy helps maintain the life cycle of restore points and make sure that backup files do not consume the entire space on the backup repository. To learn more, see [Retention Policy](mssql_retention.md).
* Force delete operation. When running the force delete operation, Veeam Plug-In checks all associated backups (full, differential, and log) for each database in the backup file (.VAB). If at least one backup is newer than the specified number of days, Veeam Plug-In retains all backups for that database. If all backups are older than the specified number of days, it deletes all database backups. The force delete operation helps to manage backups of obsolete databases that are not backed up anymore. To learn more, see [Force Delete Operation](mssql_retention_tools_force_delete.md).


