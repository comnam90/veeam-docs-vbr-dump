---
title: "Managing Jobs"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/managing_jobs.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager acts as a single point for managing jobs from all added backup servers. Users with the Portal Administrator role can centrally manage jobs that have been previously configured on added backup servers: start, stop, retry, clone, delete jobs and edit selective job settings.

Consider the following limitations:

* Enterprise Manager does not display backup policies created with the following Veeam solutions for cloud environments:

* Veeam Backup for AWS
* Veeam Backup for Google Cloud
* Veeam Backup for Microsoft Azure

* For the following Veeam plug-ins, Enterprise Manager displays only backup copy jobs:

* Veeam Backup for Nutanix AHV
* Veeam Backup for Proxmox VE
* Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization

* For physical machines, Enterprise Manager displays the following job types:

* Both Veeam Agent backup jobs managed by Veeam Agent and Veeam Agent backup jobs managed by the backup server. For more information, see [Veeam Agents Support](em_support_physical.md).
* Backup copy jobs

In This Section

* [Viewing Jobs](reports_on_jobs.md)
* [Starting, Stopping and Retrying Jobs](starting_stopping_retrying_jobs.md)
* [Enabling and Disabling Jobs](enable_disable_job.md)
* [Editing Jobs](editing_job_settings.md)
* [Creating Active Full Backups](em_job_create_active_full.md)
* [Cloning Jobs](cloning_backup_replication_jobs.md)
* [Deleting Jobs](em_delete_job.md)

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
