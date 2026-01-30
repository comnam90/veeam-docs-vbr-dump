---
title: "Migrating First Class Disks (FCDs)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/migration_job_fcd.html"
last_updated: "5/15/2024"
product_version: "13.0.1.1071"
---

# Migrating First Class Disks (FCDs)


You can relocate First Class Disks (FCDs) between datastores using Quick Migration. Migration of FCDs supports only the vMotion method. Depending on whether FCDs that you want to migrate are attached to a VM or not, Veeam Backup & Replication defines the migration scenario:

* If FCDs are not attached, Veeam Backup & Replication will migrate only the FCDs that you have selected.
* If FCDs are attached to a VM, Veeam Backup & Replication will also look for other FCDs attached to this VM and will perform migration of these FCDs as well.

Quick Migration is not a job-driven process: it cannot be saved as a job or scheduled to run later. To initiate Quick Migration of FCDs, you must complete [FCD Quick Migration](performing_instant_fcd_recovery.md) wizard and launch the FCD Quick Migration wizard.

1. [Check prerequisites](qm_byb_fcd.md).
2. [Launch the FCD Quick Migration wizard](qm_byb_fcd.md).
3. [Select FCDs to migrate](quick_migration_fcds.md).
4. [Specify an FCD destination](quick_migration_fcd_destination.md).
5. [Finish working with the wizard](quick_migration_fcd_summary.md).


