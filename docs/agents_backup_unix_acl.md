---
title: "Backup of ACLs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_unix_acl.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Backup of ACLs


Veeam Agent for IBM AIX supports backup and restore of NFSv4 Access Control Lists (ACLs).

Veeam Agent for Oracle Solaris supports backup and restore of NFSv4 and POSIX Access Control Lists (ACLs).

Considerations and Limitations

* Veeam Agent backs up all supported ACLs automatically.
* [Veeam Agent for IBM AIX] Veeam Agent does not support backup of AIXC ACLs.
* You can restore supported ACLs during bare metal recovery or file-level restore on the Veeam Agent machine side. Consider the following about restoring ACLs:

* During bare metal recovery, Veeam Agent automatically restores all supported ACLs.
* During file-level restore, you can restore only NFSv4 ACLs.
* Restoring NFSv4 ACLs requires NFSv4 to be configured on the Veeam Agent machine. For information on enabling NFSv4 in IBM AIX, see [this Veeam KB article](https://veeam.com/kb4713).

* You cannot restore ACLs when y ou perform guest file restore in Veeam Backup & Replication.


