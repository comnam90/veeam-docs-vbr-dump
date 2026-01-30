---
title: "Step 5. Specify Point in Time"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_restore_multiple_tas_specify_pit.html"
last_updated: "8/18/2025"
product_version: "13.0.1.1071"
---

# Step 5. Specify Point in Time


At this step of the wizard, specify a point in time to which you want to restore the selected SAP HANA databases.

1. In the Date field, specify the date and time of the state to which you want to restore your databases.
2. From the Time zone drop-down list, select the time zone for the time specified in the Date field. By default, Veeam Explorer for SAP HANA displays the time zone of the backup server.

The Initialize log area check box is automatically selected and grayed out when you restore your data to another server, to ensure stable operation of the tenant databases on the target SAP HANA system.

This action removes all log segments in the log area or, in other words, clears the part of the system memory that temporarily stores transaction logs before they are moved to the log backups. The database is restored to the latest available log backup before the selected point in time.

1. Click Restore.

Each database will be restored to the most recent available state to the date and time selected in the Date field. Note that if any of the databases that you want to restore were first backed up after the specified point in time, their restore process will fail.

[![Specifying Point in Time](images/vehana_specify_multiple_recovery_tas.webp)](images/vehana_specify_multiple_recovery_tas.webp "Specifying Point in Time")


