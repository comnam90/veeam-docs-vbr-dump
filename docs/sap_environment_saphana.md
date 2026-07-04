---
title: "SAP Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_environment_saphana.html"
last_updated: "6/26/2026"
product_version: "13.0.2.29"
---

# SAP Environment Planning


Keep in mind the following requirements and limitations for your SAP environment, before you deploy Veeam Plug-In for SAP HANA.

Data Channel Allocation

To control the number of parallel channels used for each SAP HANA Backint instance, edit the parallel\_data\_backup\_backint\_channels parameter in the SAP HANA global.ini file. For detailed instructions on how to edit the number of channels used in parallel, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/18db704959a24809be8d01cc0a409681.html?locale=en-US).

|  |
| --- |
| Note |
| The application of multiple streaming channels applies to all data backup services larger than 128 GB. Data backup services smaller than 128 GB use only one channel. |

Additionally, consider the following limitations when using of multiple channels:

* It is not recommended to use more than 64 channels in parallel as the overhead will reduce individual channel performance. Set the max\_recovery\_backint\_channels setting in global.ini to 64 or below depending on available hardware resources.
* It is recommended to use a separate backup repository for Veeam Plug-In backups.
* If you want to improve backup performance, the SAP HANA buffer must be increased for additional used channels. For details, consult with your SAP HANA database administrator.

* SAP HANA can back up individual databases and tenants in parallel. To optimize resources, you can back up databases sequentially.
* If there are not enough available repository task slots, SAP HANA waits till repository task slots become available.
* During restore, the order of repository task slots is ignored, and channels are used as requested by SAP HANA.

* Veeam Backup & Replication server: during manual metadata operations such as [import of backup files](import_backup_files.md), the Veeam Backup & Replication server needs additional 15 GB of RAM per 1 million files located in the same backup job folder.

Example 1: Backing up all databases in parallel

In this example, the system has 2 tenant databases, each database has 4 services. The databases are backed up in parallel. The SAP HANA channel setting is 6. The following channels are used:

* Up to 4 channels are used by SYSTEMDB and its 4 services (all below 128 GB).
* Up to 6 channels are used for the index service of the tenant database 1 (the database is bigger than 128 GB).
* Up to 3 channels are used for the rest of the 3 remaining services of the tenant database 1 (all below 128 GB).
* Up to 6 channels are used for the index service of the tenant database 2 (the database is bigger than 128 GB).
* Up to 3 channels are used for the rest of the 3 remaining services of the tenant database 2 (all below 128 GB).
* If the log backups are below 128 GB, you must reserve at least 3 channels for the log backup of SYSTEMDB, tenant database 1, and tenant database 2. These log backups are started automatically on their own schedule or when the maximum file size of the log file is reached.

In total, 27 channels were used. For backup processes of all databases started in parallel, up to 27 task slots must be available.

Example 2: Backup of all databases sequentially

In this example, the system has 2 tenant databases, each database has 4 services. The databases are backed up sequentially. The SAP HANA channel setting is 6. The following maximum repository task slots and SAP channels are used:

* Up to 6 channels are used for the index service of a tenant database (the database is bigger than 128 GB).
* Up to 3 channels are used for the rest of the 3 remaining services of the same tenant database (all below 128 GB).
* If the log backups are below 128 GB, you must reserve at least 3 channels for the log backup of SYSTEMDB, tenant database 1, and tenant database 2. These log backups are started automatically on their own schedule or when the maximum file size of the log file is reached. Assuming that the log file backups are below 128 GB and do not use additional channels.

In total, 12 channels were used. For backup processes of sequential started database backups, up to 12 task slots must be available.

Scheduling

You can schedule backup operations with all SAP HANA relevant scheduling options like SAP HANA Cockpit (HANA Cockpit 2.0 SPS 06 or later version), SAP DB13 (NW 7.02 SP17 or later version) or external schedulers like cron, UC4, TWS and others. Veeam Plug-In forwards the backups created by SAP HANA integrated backup application to a Veeam backup repository.

To learn how to configure external schedulers, see the [Veeam Plug-In for SAP HANA Best Practices](https://www.veeam.com/blog/optimize-backup-sap-hana-backint.html).

SAP HANA encryption

Veeam Plug-In supports SAP HANA integrated encryption. The encryption processes are performed on the SAP HANA side. Veeam Plug-In is not involved in encryption processing.

Plan the protection of the encryption environment. In case you loose the encryption keys, Veeam Plug-In can only provide an access to the encrypted backup file. To regain full access to the backup files, you will have to decrypt data in your SAP HANA environment. For more information on SAP HANA data encryption, see [this SAP article](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/2.0.03/en-US/8b39eaf4af7a422e9ffd48a62c2558ce.html).

SAP HANA Catalog Backup with Backint

To back up the SAP HANA catalog using Backint, change the settings of the catalog\_backup\_using\_backint parameter in the backup section of the global.ini file. To learn more, see this [SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/ac0804c23d584e2a892ee3c0a67b7e7c.html?version=2.0.03).

SAP HANA Scale-Out Cluster

Consider the following limitations of Veeam Plug-In support for SAP HANA scale-out clusters:

* All backup tasks across the SAP HANA scale-out cluster are performed in parallel.
* On all cluster nodes, Veeam Plug-In must be configured to transfer backups to the same repository.
* Due to the design of SAP HANA databases, the same Veeam Plug-In configuration must be set on all scale-out cluster members, including stand-by nodes.

* Each cluster node must use the same credentials to connect to Veeam servers.


