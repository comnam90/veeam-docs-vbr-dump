---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_protection_limitations.html"
last_updated: "10/18/2024"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Before you back up IBM Db2 databases, consider the following prerequisites:

* If you reconfigured the logarchmeth1 parameter, IBM Db2 switches the database into the BACKUP\_PENDING state. To resolve this, you must perform a full offline backup of database. After offline backup is created, you can delete the backup file and back up database online.
* If you plan to back up databases with the HADR replication, make sure that HADR is set up and initialized for all databases you want to protect. For details, see [this IBM article](https://www.ibm.com/support/pages/step-step-procedure-set-hadr-replication-between-db2-databases).

* Backups created by Veeam Plug-Ins cannot be used as a source for file to tape or backup to tape jobs.


