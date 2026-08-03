---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuration_restore_console_limitations.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Considerations and Limitations


Before you restore configuration of a backup appliance, consider the following:

* Make sure there are no sessions currently running on the backup appliance. Also, make sure there are no backup policies scheduled to run during restore. Otherwise, backups created by these policies may be corrupted.
* If the backup appliance requires an upgrade, perform it before you start configuration restore. Otherwise, Veeam Backup & Replication will not be able to perform the restore operation. To learn how to upgrade appliances, see [Updating Appliances Using Console](azure_updating_console.md).
* If you remove the backup appliance from the backup infrastructure, you will not be able to restore its configuration. However, you will be able to restore the configuration to another backup appliance currently added to the backup infrastructure.
* If you want to restore the configuration of the backup appliance to another one, you must remove the initial appliance from the backup infrastructure beforehand.
* Make sure that repositories added to the backup appliance are not managed by any other appliances. Otherwise, retention sessions running on different appliances may corrupt backup files stored in the repositories, which may result in unpredictable data loss.

* The appliance to which you restore the configuration preserves its TLS certificate.

* [Applies only if you restore the configuration of the backup appliance to another one] During restore, Veeam Backup & Replication removes the appliance and its repositories from the backup infrastructure. If the restore operation fails, re-add the appliance and its repositories to the backup infrastructure.

Page updated 2025-10-29

