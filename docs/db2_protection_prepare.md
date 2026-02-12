---
title: "Preparing Database"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_protection_prepare.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Preparing Database


Before you create a backup of the database, make sure that the database is configured properly. You must re-configure the database if you plan to perform the following operations:

* [Create incremental backups](#increment).
* [Delete backups using IBM Db2 built-in tools](#pruning).
* [Compress archive log backups](#compress).

Preparation for Incremental Backups

If you plan to create incremental backups later, set the trackmod parameter with the following command:

|  |
| --- |
| db2 update database cfg for <database\_name> using trackmod YES |

where <database\_name> is the name of the database you want to back up.

If you do not set the trackmod parameter and create a full backup, you will not be able to create incremental backups for this full backup.

Preparation for Backup Pruning

If you plan to delete backups using the PRUNE HISTORY command later, set the AUTO\_DEL\_REC\_OBJ parameter with the following command:

|  |
| --- |
| db2 update database cfg for <database\_name> using AUTO\_DEL\_REC\_OBJ ON |

where <database\_name> is the name of the database you plan to back up.

If you do not set the AUTO\_DEL\_REC\_OBJ parameter and create backups, you will not be able to delete these backups from the backup repository using the PRUNE HISTORY command. Without this parameter, IBM Db2 deletes backups only from the database internal history.

Compression of Archive Log Backups

IBM Db2 supports compression of archive log backups. By default, the compression is disabled. You can enable the compression for the database with the following command:

|  |
| --- |
| db2 update database cfg for <database\_name> using logarchcompr1 ON |

where <database\_name> is the name of the database you want to back up.

Alternatively, you can set IBM Db2 to use hardware-accelerated compression. To do this, run the following command:

|  |
| --- |
| db2 update database cfg for <database\_name> using logarchcompr1 ZLIB |

where <database\_name> is the name of the database you want to back up.


