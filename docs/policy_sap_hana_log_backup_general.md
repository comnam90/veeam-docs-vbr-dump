---
title: "Processing Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_sap_hana_log_backup_general.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Processing Settings

In this article

To specify processing settings for the object:

1. At the Log Backup step of the wizard, select the object and click Edit.
2. In the Processing tab, select the way you want to back up logs:

* Select Let SAP HANA manage log backup if you want to back up logs with SAP HANA tools.

With SAP HANA tools, you set to back up logs by Veeam Plug-In and set the log backup interval. In this case Veeam Plug-In will backup logs with parameters specified with SAP HANA tools. You can also set SAP HANA tools not to back up logs. In this case Veeam Plug-In will not back up logs too.

* Select Perform log backup with this policy if you want to back up logs with Veeam Plug-In.

In the Backup logs every <N> minutes field, specify the frequency for logs backup. By default, redo logs are backed up every 15 minutes. The minimum log backup interval is 5 minutes. The maximum log backup interval is 480 minutes.

![Processing Settings](images/policy_sap_hana_log_backup_processing.webp)

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
