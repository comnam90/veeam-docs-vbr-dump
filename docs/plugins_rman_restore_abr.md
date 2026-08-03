---
title: "Restore from Application Backup Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_rman_restore_abr.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restore from Application Backup Repository


If you use Oracle RMAN Incremental Merge, you can recover an Oracle database using the image copy and incremental backups stored on the NFS share of the application backup repository. For more information, see [Oracle RMAN Incremental Merge](plugins_rman_incremental_merge_overview.md).

Depending on the recovery scenario, you can use the image copy and application backup repository snapshots in the following ways:

* Switch the database to the image copy stored on the NFS share. This approach allows you to minimize the downtime in case of disaster. Since the image copy contains ready-to-use database files, Oracle RMAN will only update the control file to use the image copy as the current database files and will not copy any data. After the switch, the database will run directly from the NFS share until you restore the database files to the production storage. For more information, see [Switching Database to Image Copy](#switching_database).
* Recover the database from the NFS share to the production storage, without switching the database to the image copy. In this case, Oracle RMAN will copy the database files from the NFS share to their original location, and the restore operation will take about as much time as a full database restore. For more information, see [Restoring Database to Production Storage](plugins_rman_restore_abr.md#restore_db).
* Restore the database to another server. You can export the data of an application backup repository snapshot to a temporary NFS share and restore the database from this share without changing the production database. This maybe useful for testing purposes. For more information, see [Restoring Database to Another Server](plugins_rman_restore_abr.md#restore_another_server).

Switching Database to Image Copy

To switch the database to the image copy, run the following command:

|  |
| --- |
| RUN { SHUTDOWN IMMEDIATE; STARTUP MOUNT; SWITCH DATABASE TO COPY; RECOVER DATABASE; ALTER DATABASE OPEN; } |

After you switch the database to image copy, make sure you disable the snapshot schedule in the repository settings . You cannot create snapshots of the share while the database is running.

To return the database files to the production storage later, run the following statement for each database file:

|  |
| --- |
| ALTER DATABASE MOVE DATAFILE '<file\_path>' TO '<new\_file\_path>'; |

where:

* <file\_path> is the current path of the database file on the NFS share.
* <new\_file\_path> is the path on the production storage to which Oracle will move the database file.

For example:

|  |
| --- |
| ALTER DATABASE MOVE DATAFILE '/nfsabr/oracopy/ORCL\_USERS\_4.dbf' TO '/u01/oradata/ORCL/users01.dbf'; |

Restoring Database to Production Storage

To restore the database from the image copy, run the following command:

|  |
| --- |
| RUN { SHUTDOWN IMMEDIATE; STARTUP MOUNT; RESTORE DATABASE FROM TAG '<tag\_name>'; RECOVER DATABASE; ALTER DATABASE OPEN; } |

where <tag\_name> is the tag of the image copy from which Oracle RMAN restores the database. Specify the tag that you used when you created the image copy. For more information, see [Oracle RMAN Incremental Merge](plugins_rman_incremental_merge_overview.md).

For example:

|  |
| --- |
| RUN { SHUTDOWN IMMEDIATE; STARTUP MOUNT; RESTORE DATABASE FROM TAG 'X'; RECOVER DATABASE; ALTER DATABASE OPEN; } |

Alternatively, you can recover the application backup repository to an earlier snapshot and switch the database to the image copy from this snapshot. After the recovery operation, you must restore the control file from the backup stored on the share. For more information on this operation, see [Performing Instant Application Backup Repository Recovery](performing_abr_recovery.md).

Restoring Database to Another Server

To restore the database to another server, do the following:

1. In the Veeam Backup & Replication console, export the data of the required snapshot to a temporary NFS share. For more information, see [Performing Instant Application Backup Repository Recovery](performing_abr_recovery.md).
2. Mount the temporary NFS share on the target server.
3. On the target server, restore the database from the image copy stored on the share. To restore the database, run the following command:

|  |
| --- |
| RUN { STARTUP NOMOUNT; RESTORE SPFILE FROM '<mount\_point>/spfile/<file\_name>'; SHUTDOWN IMMEDIATE; STARTUP NOMOUNT; RESTORE CONTROLFILE FROM '<mount\_point>/controlfile/<file\_name>'; ALTER DATABASE MOUNT; CATALOG START WITH '<mount\_point>/oracopy' NOPROMPT; CATALOG START WITH '<mount\_point>/archlogs' NOPROMPT; RESTORE DATABASE; RECOVER DATABASE; ALTER DATABASE OPEN RESETLOGS; } |

where:

* <mount\_point> is the mount point of the temporary NFS share on the target server.
* <file\_name> is the name of the backup file on the share. Make sure that you restore the SPFILE and control file that match the image copy in the snapshot.

For example:

|  |
| --- |
| RUN { STARTUP NOMOUNT; RESTORE SPFILE FROM '/tempabr/spfile/ORCL\_spfile.bkp'; SHUTDOWN IMMEDIATE; STARTUP NOMOUNT; RESTORE CONTROLFILE FROM '/tempabr/controlfile/ORCL\_ctrl.bkp'; ALTER DATABASE MOUNT; CATALOG START WITH '/tempabr/oracopy' NOPROMPT; CATALOG START WITH '/tempabr/archlogs' NOPROMPT; RESTORE DATABASE; RECOVER DATABASE; ALTER DATABASE OPEN RESETLOGS; } |

Oracle RMAN will restore the database files to the paths recorded in the control file. Make sure that these paths exist on the target server.

When you stop the export session, Veeam Backup & Replication deletes the temporary NFS share together with all the data stored on it.

Page updated 2026-07-24

