---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_about.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Overview


Epic EHR (Electronic Health Record) uses the InterSystems IRIS data platform as the core database engine for EHR systems to manage large volumes of healthcare data. Epic EHR System Protection in Veeam Backup & Replication provides protection for InterSystems IRIS databases.

Epic EHR System Protection consists of the following components:

* Protection group for InterSystems IRIS databases rolls out components on ODB (operational database) servers to rescan the application topology.
* Backup policy for InterSystems IRIS databases backs up data from storage snapshots to a backup repository, or retains only the storage snapshots in snapshot-only mode.
* Restore wizard enables restore to the original or to a different location.

In This Section

* [Solution Architecture](iris_hiw.md)
* [Computer Discovery and Veeam Components Deployment](iris_discovery_and_deployment.md)
* [Application Backup Policies](iris_backup_job.md)
* [Data Backup](iris_data_backup.md)
* [Data Restore](iris_data_restore.md)

* [Backup to Object Storage](iris_object_storage.md)

Page updated 2026-07-28

