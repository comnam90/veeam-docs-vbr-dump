---
title: "Getting Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_support.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# Getting Support


If you have any questions or issues with Veeam Explorer for MongoDB, you can visit [Veeam R&D Forums](https://forums.veeam.com) or submit a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

Before you submit a support ticket, make sure that comprehensive information is provided to the Veeam Support Team. To do this, take the following steps:

1. Perform the problematic operation with the extended logging mode enabled. For more information, see [Enabling Extended Logging](vemdb_extended_logs.md).
2. Use the Export Logs wizard as described in [Exporting Logs](exporting_logs.md). Make sure to export all logs for the relevant backup infrastructure components.
3. Collect logs for the components deployed on the target machine for the restore operation.

1. Save the /tmp/mongod.log file to get logs for the temporary MongoDB instance.
2. Save the /root/.local/share/VeeamBackup/MongoDBAgent/Logs folder to get logs for the Veeam MongoDB Restore Agent.


