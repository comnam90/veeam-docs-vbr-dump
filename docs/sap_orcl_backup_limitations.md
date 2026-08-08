---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_backup_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


Before you start using Veeam Plug-In for SAP on Oracle, consider the following:

* You can make incremental backups only with the rman\_util parameter. For details, see [this SAP article](https://help.sap.com/doc/saphelp_nw74/7.4.16/en-us/47/3b8f17fae93423e10000000a1553f6/content.htm?no_cache=true). To learn how to perform an incremental backup, see [Incremental Backup](sap_orcl_incr.md).
* Automatic Storage Management (Oracle ASM) is supported only with the rman\_util parameter. If you want to back up Oracle ASM instances, see [SAP on Oracle Backup Using RMAN\_UTIL](rman_util.md).

* You cannot back up Oracle RAC databases using the BRBACKUP tool.
* Volume backup (-d util\_vol, util\_vol\_online) is not supported.
* Backup of directories is not supported.

* Backups created by Veeam Plug-Ins cannot be used as a source for file to tape jobs. For information about backup to tape support, see [Backup to Tape](plugins_sap_orcl_backup_to_tape.md).

Page updated 2026-07-10

