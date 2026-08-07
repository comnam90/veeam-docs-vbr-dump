---
title: "Application Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/application_backup_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Application Backup Repositories


An application backup repository is based on Veeam Hardened Repository and intended for application backup storage.

An application backup repository is a smart NFS share — it protects any application data written to an NFS share mounted on the application backup repository host. Veeam Backup & Replication controls who can access the share, creates immutable file-system snapshots of the share on a regular basis, turns the snapshots into restore points and applies the retention policy. The data can then be transformed into a regular Veeam backup chain using backup copy jobs and archived to tapes. For data recovery scenarios, you can revert the application backup repository data to a point in time using snapshots or export the data to a temporary NFS share for browsing and selective restore.

In the application backup repository, you can store the data of the following applications:

* Native incremental database solutions: Oracle Incremental Merge, and others.
* Containerized applications: Proxmox LXC, Docker, and others.
* DBaaS solutions: MongoDB Atlas, Superbase, and others.
* Configuration data of network devices: firewall or switch configurations.
* Custom in-house applications.
* Any other application with native export capabilities that can write its data directly to the target NFS share.

In This Section

* [Considerations and Limitations](abr_limitations.md)
* [How Application Backup Repository Works](abr_hiw.md)
* [Deploying Application Backup Repository](deploy_abr.md)
* [Adding Application Backup Repositories](abr_repository_add.md)
* [Backup Copy Jobs for Application Backup Repositories](bcj_abr_repository.md)
* [Performing Instant Application Backup Repository Recovery](performing_abr_recovery.md)
* [Creating Snapshots Manually](abr_creating_snapshots.md)
* [Rescanning Application Backup Repositories](rescanning_abr.md)
* [Removing Application Backup Repositories](removing_abr.md)

Page updated 2026-07-29

