---
title: "Epic EHR System Protection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Epic EHR System Protection


Epic EHR System Protection provides application-aware protection of Epic Electronic Health Record (EHR) deployments running on the InterSystems IRIS Data Platform. Instead of backing up through a hypervisor, Veeam Backup & Replication protects the application at the storage level over the Universal Storage API. Veeam Backup & Replication creates storage snapshots of the volumes that store the InterSystems IRIS databases, mounts them to a Linux-based backup proxy and reads the data with the unstructured data backup engine.

In This Section

* [Overview](iris_about.md)
* [Planning and Preparation](iris_planning_and_preparation.md)
* [Getting Started](iris_getting_started.md)
* [Configuring Security Settings](iris_security_settings.md)
* [Working with Protection Group](iris_protection_group.md)
* [Working with Application Backup Policy for InterSystems IRIS Instances](iris_policy.md)
* [Managing Protected ODB Servers](iris_protected_odb.md)
* [Managing Application Backups](iris_application_backups.md)
* [Managing License](iris_managing_license.md)
* [Reporting](iris_report.md)
* [Backup Retention](iris_retention.md)
* [Logs and Support](iris_veeam_logs.md)

Page updated 2026-07-29

