---
title: "Oracle RMAN Incremental Backup and Merge"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_rman_incremental_merge.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Oracle RMAN Incremental Backup and Merge


Prev1/1Next

With Oracle RMAN Incremental Merge, you can maintain an up-to-date image copy of an Oracle database in an application backup repository. To do so, perform the following:

1. Before you start working with the Oracle server, make sure you added an application backup repository to the Veeam Backup & Replication backup infrastructure and mounted the NFS share of the application backup repository on the Oracle server.

For more information, see [Oracle RMAN Incremental Merge](plugins_rman_incremental_merge_overview.md).

1. On the Oracle server, create an image copy of the database with a level 0 incremental backup. To do this, run the following command:

|  |
| --- |
| RUN { ALLOCATE CHANNEL <channel\_name> DEVICE TYPE DISK; SQL "ALTER SYSTEM ARCHIVE LOG CURRENT"; BACKUP INCREMENTAL LEVEL 0 AS COPY DATABASE TAG '<tag\_name>' FORMAT '<mount\_point>/oracopy/%d\_%N\_%f.dbf'; BACKUP ARCHIVELOG ALL NOT BACKED UP FORMAT '<mount\_point>/archlogs/%d\_arch\_%t\_%U'; BACKUP CURRENT CONTROLFILE FORMAT '<mount\_point>/controlfile/%d\_ctrl.bkp' REUSE; BACKUP SPFILE FORMAT '<mount\_point>/spfile/%d\_spfile.bkp' REUSE; RELEASE CHANNEL <channel\_name>; } |

where:

* <mount\_point> is the mount point of the application backup repository NFS share.
* <channel\_name> is the name of the RMAN channel. To run the backup process in parallel, you can allocate multiple channels.
* <tag\_name> is the tag that identifies the image copy of the database. Use the same tag for level 1 incremental backups so that Oracle RMAN merges them into this image copy.

For example:

|  |
| --- |
| RUN { ALLOCATE CHANNEL ch1 DEVICE TYPE DISK; SQL "ALTER SYSTEM ARCHIVE LOG CURRENT"; BACKUP INCREMENTAL LEVEL 0 AS COPY DATABASE TAG 'X' FORMAT '/nfsabr/oracopy/%d\_%N\_%f.dbf'; BACKUP ARCHIVELOG ALL NOT BACKED UP FORMAT '/nfsabr/archlogs/%d\_arch\_%t\_%U'; BACKUP CURRENT CONTROLFILE FORMAT '/nfsabr/controlfile/%d\_ctrl.bkp' REUSE; BACKUP SPFILE FORMAT '/nfsabr/spfile/%d\_spfile.bkp' REUSE; RELEASE CHANNEL ch1; } |

1. Schedule regular level 1 incremental backups. During each run, Oracle RMAN will back up data blocks changed since the previous run and merge the incremental backup into the image copy. To do this, run the following command:

|  |
| --- |
| RUN { ALLOCATE CHANNEL <channel\_name> DEVICE TYPE DISK; SQL "ALTER SYSTEM ARCHIVE LOG CURRENT"; BACKUP INCREMENTAL LEVEL 1 FOR RECOVER OF COPY WITH TAG '<tag\_name>' DATABASE FORMAT '<mount\_point>/incrementbackup/%d\_icr\_%t\_%U'; RECOVER COPY OF DATABASE WITH TAG '<tag\_name>'; RELEASE CHANNEL <channel\_name>; } |

where:

* <mount\_point> is the mount point of the application backup repository NFS share.
* <channel\_name> is the name of the RMAN channel. To run the backup process in parallel, you can allocate multiple channels.
* <tag\_name> is the tag of the image copy into which Oracle RMAN merges the incremental backup. Specify the tag that you used when you created the image copy.

For example:

|  |
| --- |
| RUN { ALLOCATE CHANNEL ch1 DEVICE TYPE DISK; SQL "ALTER SYSTEM ARCHIVE LOG CURRENT"; BACKUP INCREMENTAL LEVEL 1 FOR RECOVER OF COPY WITH TAG 'X' DATABASE FORMAT '/nfsabr/incrementbackup/%d\_icr\_%t\_%U'; RECOVER COPY OF DATABASE WITH TAG 'X'; RELEASE CHANNEL ch1; } |

|  |
| --- |
| Tip |
| In addition to the schedule, you can create application backup repository snapshots manually. Such a snapshot produces a restore point with the latest state of the image copy. For details, see [Creating Snapshots Manually](abr_creating_snapshots.md). |

Page updated 2026-07-24

