---
title: "Restoring Tenant Databases with SAP HANA Cockpit"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_tenantdb_cockpit.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---

# Restoring Tenant Databases with SAP HANA Cockpit

In this article

You can restore SAP HANA tenant databases from the Veeam Plug-In backups using SAP HANA Cockpit.

The example below is provided for demonstration purposes only. For details on the full restore functionality of SAP HANA tools, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/6cc445744848464e836d73a61e84ea00.html?locale=en-US&version=2.0.05).

To perform a Backint recovery of an SAP HANA tenant database from a Veeam Plug-In backup, do the following:

1. In the System Overview page of the required system, click Manage Databases.

[![System Overview](images/tenant_recovery_manage_dbs.webp)](images/tenant_recovery_manage_dbs.webp "System Overview")

1. In the Manage Databases page, expand the toolbar options and select Recover Tenant.

[![Manage Databases](images/tenant_recovery_launch.webp)](images/tenant_recovery_launch.webp "Manage Databases")

1. After you launch the recovery wizard, SAP HANA will issue the warning that the database must be stopped for recovery. Click Stop Tenant in the warning window.
2. At the Recovery Target step of the wizard, select the required restore point and click Step 2.

[![Recovery Target](images/tenant_recovery_target.webp)](images/tenant_recovery_target.webp "Recovery Target")

1. Specify the location of the latest backup catalog and click Step 3.

[![Specify Backup Location](images/tenant_recovery_catalog_location.webp)](images/tenant_recovery_catalog_location.webp "Specify Backup Location")

1. At the Backup to be Used step, select the backup and click Step 4.

[![Backup to be Used](images/tenant_recovery_select_backup.webp)](images/tenant_recovery_select_backup.webp "Backup to be Used")

1. At the Delta Backups step, select Yes to use delta backups.

[![Delta Backups](images/sysdb_recovery_delta_backups.webp)](images/sysdb_recovery_delta_backups.webp "Delta Backups")

1. At the Specify Alternative Backup Locations step, if you want to use backups that are not included in the backup catalog, specify their locations. You can also change the location for log backups.

If you leave the fields empty, SAP HANA will use the locations specified in the backup catalog.

[![Specify Alternative Backup Locations](images/tenant_recovery_alternative_backup_location.webp)](images/tenant_recovery_alternative_backup_location.webp "Specify Alternative Backup Locations")

1. Select Yes or No, to check if the backups are available. Note that at this stage SAP HANA does not check the integrity of the backup content on the block level.

[![Check Availability of Backups](images/tenant_recovery_check_availability.webp)](images/tenant_recovery_check_availability.webp "Check Availability of Backups")

1. Select No to initialize the log area and click Review. You must initialize the log area only if the log area is unavailable or if you are recovering the database to a different system.

[![Initialize Log Area](images/tenant_recovery_initialize_log_area.webp)](images/tenant_recovery_initialize_log_area.webp "Initialize Log Area")

1. Review the recovery options and click Start Recovery.

[![Review Recovery Options](images/tenant_recovery_review.webp)](images/tenant_recovery_review.webp "Review Recovery Options")

Page updated 12/20/2024

Page content applies to build 13.0.1.1071
