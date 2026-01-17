---
title: "Guest Processing Options"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdp_guestprocessingoptions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The GuestProcessingOptions element contains the following guest processing options.

| Element | Type | Description |
| --- | --- | --- |
| VssSnapshotOptions | VssSnapshotOptionsType | Application-aware processing options. For details, see [Application-Aware Processing Options](#vss). |
| WindowsCredentialsId | String | ID of guest OS credentials for starting the indexing runtime process in Microsoft Windows OS. |
| LinuxCredentialsId | String | ID of guest OS credentials for starting the indexing runtime process in Linux OS. |

Application-Aware Processing Options

The VssSnapshotOptions element contains the following application-aware processing options.

| Element | Type | Description |
| --- | --- | --- |
| VssSnapshotMode | String | Mode of application-aware image processing. Possible values:   * RequireSuccess * IgnoreFailures * Disabled |
| IsCopyOnly | Boolean | Defines whether copy-only backups must be created or transaction logs for Microsoft Exchange, Microsoft SQL and Oracle VMs must be processed. Possible values:   * True * False |
| UsePersistentGuestAgent | Boolean | Defines whether to use persistent guest agents on the protected VM for application-aware processing. Possible values:   * True * False   The default value is False. |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
