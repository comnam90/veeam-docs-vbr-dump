---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restoring_veeam_explorers_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you recover application items, consider the following:

* The backup or replica you plan to restore from must be created with application-aware processing enabled. For more information, see the Specify Guest Processing Settings step of the job or policy wizard for the relevant hypervisor, cloud or physical platform. For example, see [Specify Guest Processing Settings](backup_job_vss_vm.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication console or [Specify Guest Processing Settings](backup_job_vss_vm_web.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication web UI.
* For recovery from storage snapshots, check the requirements in [Data Recovery from Storage Snapshots](storage_limitations_general.md#vess).
* For recovery from VeeamZIP backups, check the requirements in [VeeamZIP](veeamzip.md).
* For requirements and limitations during restore see the relevant Explorer sections.

* [Microsoft Active Directory](vead_prerequisites.md)
* [Microsoft SQL Server](https://helpcenter.veeam.com/docs/vbr/explorers/vesql_prerequisites.html?ver=13)
* [Oracle](https://helpcenter.veeam.com/docs/vbr/explorers/veo_prerequisites.html?ver=13)
* [PostgreSQL](https://helpcenter.veeam.com/docs/vbr/explorers/vep_prerequisites.html?ver=13)
* [Microsoft Exchange](https://helpcenter.veeam.com/docs/vbr/explorers/vex_prerequisites.html?ver=13)
* [Microsoft SharePoint](https://helpcenter.veeam.com/docs/vbr/explorers/vesp_prerequisites.html?ver=13)
* [Microsoft OneDrive](https://helpcenter.veeam.com/docs/vbr/explorers/veod_planning_and_prep.html?ver=13)
* [Microsoft Teams](https://helpcenter.veeam.com/docs/vbr/explorers/vet_prerequisites.html?ver=13)

Page updated 2026-05-27

