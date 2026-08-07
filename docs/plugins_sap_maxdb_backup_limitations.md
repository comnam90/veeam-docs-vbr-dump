---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_backup_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


Before you back up SAP MaxDB with Veeam Plug-In, consider the following:

* Volume backup (-d util\_vol, util\_vol\_online) is not supported.
* Backup of directories is not supported.

* Backups created by Veeam Plug-Ins cannot be used as a source for file to tape jobs. For information about backup to tape support, see [Backup to Tape](plugins_sap_maxdb_backup_to_tape.md).

* Review backup prerequisites in [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_7/ea/1a116bb3c6428ebbcaff211686be7a/frameset.htm).

Page updated 2026-07-10

