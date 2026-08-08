---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


Before you start using Veeam Plug-In for Oracle RMAN, consider the following:

* Backups created by Veeam Plug-Ins cannot be used as a source for file to tape jobs. For information about backup to tape support, see [Backup to Tape](plugins_rman_backup_to_tape.md).

* In the Veeam Plug-In configuration wizard, you can enable/disable Veeam Plug-In Data Compression and Deduplication. If you enable the Veeam Plug-In compression, do not use Oracle RMAN integrated compression as well. It can slow down the backup and restore processes.
* It is an Oracle best practice to add the EXIT; command at the bottom of the script to shut down the RMAN utility. Without the EXIT; command in the script, it is up to Oracle RMAN to decide when to close the backup session, which can lead to multiple unclosed RMAN backup sessions.

* The progress bar of a running Oracle database backup job is available only for backups of standalone Oracle databases. It is not available for Oracle RAC backups.

Page updated 2026-07-10

