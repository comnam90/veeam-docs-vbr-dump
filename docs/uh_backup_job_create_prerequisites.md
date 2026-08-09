---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_backup_job_create_prerequisites.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you create a backup job, consider the following limitations:

* You can back up each VM with one backup job at a time. If a VM is already being processed by a backup job, another backup job will not start processing this VM until the currently running backup operation completes.

* You cannot back up the universal hypervisor manager VM and Veeam worker VMs.
* You cannot back up a VM being restored. Wait for the restore process to complete, and then start the backup job.

* You cannot include into a backup job a VM that is being backed up by 3rd party software. Wait for the backup process to complete or stop the currently running job manually, and then add the VM to the necessary backup job.

* By default, [backup encryption](data_encryption.md) is disabled for backed-up data. However, you can enable encryption at the repository level as described in section [Access Permissions](access_permissions.md).

* Since Veeam Backup & Replication does not allow you to assign [information about locations](locations.md) to the Universal Hypervisor Manager and workers, job statistics do not include information on the universal hypervisor VM data migration between different geographic regions.

Page updated 2026-07-24

