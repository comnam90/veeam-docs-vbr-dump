---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_config_restore_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you restore the appliance configuration database of a backup appliance, consider the following:

* Make sure there are no sessions currently running on the backup appliance. Also, make sure there are no backup policies scheduled to run during restore. Otherwise, backups created by these policies may be corrupted.

* If the backup appliance requires an upgrade, perform it before you start configuration restore. Otherwise, Veeam Backup & Replication will not be able to perform the restore operation. To learn how to upgrade appliances, see [Updating Appliances Using Console](aws_upgrade_appliance_console.md).

* If you remove the backup appliance from the backup infrastructure, you will not be able to restore its configuration. However, you will be able to restore the configuration to another backup appliance currently added to the backup infrastructure.
* If you want to restore the configuration to another backup appliance, you must remove the initial appliance from the backup infrastructure beforehand.

* Make sure that repositories added to the restored backup appliance are not managed by any other backup appliances. Otherwise, retention sessions running on different appliances may corrupt backup files stored in the repositories, which may result in unpredictable data loss.

* The appliance to which you restore the configuration preserves its TLS certificate.
* [Applies only if you restore the configuration to another backup appliance] During restore, Veeam Backup & Replication removes the initial appliance and its repositories from the backup infrastructure. If the restore operation fails, re-add the appliance and its repositories to the backup infrastructure.

Page updated 2026-05-21

