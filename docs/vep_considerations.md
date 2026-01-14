---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_considerations.html"
last_updated: "12/23/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

This section lists considerations and known limitations of Veeam Explorer for PostgreSQL.

General

* High availability cluster configurations and replication setups of PostgreSQL servers are not supported.
* Veeam Explorer for PostgreSQL does not support recovery operations over VIX API or vSphere Automation API.
* Recovery of databases that reside in an encrypted file system on the source machine is not supported. In particular, encrypted LVM volumes are not supported.
* You can recover PostgreSQL data over SSH only, restore using Linux Management Agent is not supported.
* Veeam Explorer for PostgreSQL does not support data recovery from backed-up machines that have 3rd party PostgreSQL variants or extensions installed.
* With Veeam Explorer for PostgreSQL, you can only recover PostgreSQL data from backups of powered-on machines and from instances that were running at the time of backup.

* Restore, publishing, instant recovery, and export operations of PostgreSQL instances or databases to a point-in-time state require backups of PostgreSQL write ahead log (WAL) files. To allow Veeam Backup & Replication to create PostgreSQL WAL file backups, PostgreSQL instances must have the replica wal\_level setting or higher. The minimal wal\_level setting does not write information about database transactions and it allows you to create a crash-consistent backup only.

* Restore, publishing, instant recovery, and export operations of PostgreSQL data from replicas can only recover your data to the latest state of the selected restore point. Replication jobs do not copy PostgreSQL write ahead log (WAL) files so data recovery to a point-in-time state is not supported.

* When recovering your PostgreSQL data from CDP replicas, consider the following limitations:

* Restore, publishing, instant recovery, and export operations of PostgreSQL data from CDP replicas can only recover your data to the latest state of the selected long-term restore point. CDP policies do not copy PostgreSQL write ahead log (WAL) files so data recovery to a point-in-time state is not supported.

* When you recover your data from CDP replicas, you can only use long-term (both application-consistent and crash-consistent) restore points. Short-term restore points are not supported.
* You can recover your data from a CDP replica if its CDP policy is currently running. During recovery, the CDP policy does not create new long-term restore points and does not delete existing ones. Short-term restore points are still created.
* You cannot restore application items from a CDP replica in parallel with guest OS file restore, SureReplica, and failover.

* Veeam Explorer for PostgreSQL supports SSH fingerprint validation of Linux machines used as target and staging servers. For more information on how to configure this feature, see [Host Authentication](linux_fingerprint_check.md).

If you have selected the more secure, manual validation in the Veeam Backup & Replication console, consider the following:

* If the target server is unknown or its fingerprint cannot be recognized, you will be able to proceed with the recovery operation after you manually validate the fingerprint in the Veeam Backup & Replication console.

* The validation process matches the fingerprint only with the network identifier of the Linux machine (its IPv4 address, IPv6 address, FQDN, or hostname) used in the respective Veeam Explorer for PostgreSQL session. If you use 2 different network identifiers of the same unverified server in 2 recovery sessions (for example, its IPv4 address in one recovery session and its hostname in another), you will need to perform 2 separate fingerprint validations. No further validations are necessary if you reuse a validated network identifier in another recovery session.

* In PostgreSQL 15 and earlier, Veeam Explorer for PostgreSQL does not support configuration sub-files that are specified in the include, include\_dir and include\_if\_exist options in the postgresql.conf file. All PostgreSQL configurations, instance ports in particular, must be specified in a single postgresql.conf file.

Starting from PostgreSQL 16, the pg\_hba.conf and pg\_ident.conf files can also have configuration sub-files, specified in the include, include\_dir and include\_if\_exist options. Veeam Explorer for PostgreSQL does not support these configuration sub-files either, so make sure that in PostgreSQL 16 and later all configurations are specified only in the postgresql.conf, pg\_hba.conf and pg\_ident.conf files.

Note that if the include, include\_dir and include\_if\_exist options are used, Veeam Explorer for PostgreSQL will comment them out after restore and instant recovery operations.

* The en\_US.utf8 locale must be installed on the target server. The locale is also required on the staging server for export operations.
* Interactive login scripts configured on the target server (and staging server for export operations) may interrupt the recovery process. To prevent data recovery from failure, disable the scripts.

* If PostgreSQL utilities (such as pg\_ctl, pg\_dump and pg\_basebackup) are located in custom directories on the target server (the staging server for export operations), Veeam Explorer for PostgreSQL may not find the utilities. In this case, go to the /etc/veeam/explorerstandbyservice/ (for Linux-based mount servers) or %ProgramData%\Veeam\Backup\ExplorerStandByService\ (for Windows-based mount servers) directory of the mount server. If a configuration file named config.xml (for Linux-based mount servers) or Config.xml (for Windows-based mount servers) does not exist in this directory, create this file.

In the configuration file, enter the following XML code:

|  |
| --- |
| <Veeam>     <PostgreSqlExplorer>         <PostgreSQL PostgreSqlBinariesDirectory="<path1> <path2>"/>     </PostgreSqlExplorer>  </Veeam> |

where <path1> and <path2> are paths to directories that contain PostgreSQL utilities. For example, the paths can be /directory\_name/postgres/postgres-14.10.0/bin and /var/lib/pg (note the absence of a separator at the end of the paths). You can add multiple paths, but make sure to separate them with spaces, not commas.

To finish the configuration, save the configuration file and restart the Veeam Explorers Recovery Service on the same server.

* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

Restore, Publishing and Instant Recovery

* Mount of Btrfs and ZFS disks will fail if you perform instant recovery, data restore or data publish operations to the original server. The issue occurs due to a restriction for mounting 2 Btrfs or ZFS disks with identical IDs to the same machine (the disks have the same IDs on the backup and the original server).
* With Veeam Explorer for PostgreSQL, you can restore, instantly recover and publish entire PostgreSQL instances; restore, instant recovery and publishing of individual databases is not supported.
* PostgreSQL on the target machine and on the backed-up machine must be of the same major version. For example, you can restore a PostgreSQL instance based on PostgreSQL 15.1 to a machine with PostgreSQL 15.3.
* Before you restore, instantly recover, or publish an PostgreSQL instance to another server, make sure PostgreSQL is installed on the target machine.
* [For restore and instant recovery] If you specify another data directory for the recovered PostgreSQL instance, services will not be created automatically (including systemd).
* [For restore and instant recovery on Debian and Ubuntu] When you restore a PostgreSQL instance to a new data directory, Veeam Explorer for PostgreSQL saves PostgreSQL configuration files to the specified data directory (not to the /etc/postgresql directory). In this case, you will not be able to discover the recovered PostgreSQL instance with the pg\_lsclusters utility.
* [For publishing and instant recovery] Make sure that the volume with the write cache has enough free disk space to store the changes of the published database. The write cache is stored in the /var/lib/veeam/IRCache folder on the mount server.

Export

* Exporting multiple databases one by one may cause performance issues — do so only if you need to restore each database to a different point-in-time state. To export up to a 1000 databases in parallel, start the export sessions from a published PostgreSQL instance (the only option if you use PowerShell), a backed-up PostgreSQL instance, or from the backed-up PostgreSQL server.
* Exporting databases to the local host where Veeam Explorer for PostgreSQL is running is only supported for Windows-based backup servers (Veeam Backup & Replication version 12.1 and later). If you use a Linux-based backup server, you can only export your databases to another Linux server.
* You cannot export databases whose pg\_database system catalog has the datallowconn parameter set to false. This setting prevents all connections to the database and causes export operations to fail. For example, this is the case for the template0 database, which is used to create new databases — as a template database, it must remain unchanged.
* PostgreSQL on the staging server and on the backed-up machine must be of the same major version. For example, if PostgreSQL 15.1 is installed on the backed-up machine, the staging server can have PostgreSQL 15.3.
* You can use pg\_restore to reconstruct a database from a DUMP file exported with Veeam Explorer for PostgreSQL. If a new database is created in the process and the database in the DUMP file has tablespaces, you must manually create tablespaces with the same names as the ones in the DUMP file. Note that the --no-tablespace argument of the pg\_restore utility, which places the reconstructed database in the default tablespace, is not supported for DUMP files exported with Veeam Explorer for PostgreSQL. For more information, see [Restoring Exported Database](vep_export_restore_exported_databases.md).

Page updated 12/23/2025

Page content applies to build 13.0.1.1071
