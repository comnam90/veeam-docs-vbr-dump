---
title: "Epic EHR System Protection Integration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_iris_integration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Epic EHR System Protection Integration


Veeam Backup & Replication allows you to integrate your storage systems with InterSystems IRIS Data Platform to create backups from storage snapshots or snapshots of InterSystems IRIS instances hosted on these storage systems. For more information, see [Epic EHR System Protection](iris_backup.md).

To start working with storage systems, you must properly configure the backup infrastructure. For more information, see [Infrastructure Overview](storage_infrastructure.md). After that, you can use storage snapshots for data protection and disaster recovery operations. For more information on the overall infrastructure required for Epic EHR System Protection, see [Solution Architecture](iris_hiw.md).

Supported Storage Systems

IRIS integration uses LUN-based protocols (FC, iSCSI) and is supported only on Universal Storage API integrated systems. Built-in storage systems are not supported.

For the list of storage systems that support IRIS integration, see [System Requirements](storage_system_requirements.md).

Related Topics

* [Infrastructure Overview](storage_infrastructure.md)
* [Universal Storage API Integrated Systems](universal_storage_integration_api.md)
* [Rescanning Storage Systems](storage_rescan.md)

Page updated 2026-07-28

