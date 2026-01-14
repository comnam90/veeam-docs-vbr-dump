---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_backup_limitations.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

Before you back up SAP MaxDB with Veeam Plug-In, consider the following:

* Volume backup (-d util\_vol, util\_vol\_online) is not supported.
* Backup of directories is not supported.
* Backups created by Veeam Plug-Ins cannot be used as a source for file to tape or backup to tape jobs.
* Review backup prerequisites in [SAP MaxDB documentaton](https://maxdb.sap.com/doc/7_7/ea/1a116bb3c6428ebbcaff211686be7a/frameset.htm).

Page updated 12/3/2025

Page content applies to build 13.0.1.1071
