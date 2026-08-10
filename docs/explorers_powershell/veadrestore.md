---
title: "VEADRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veadrestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VEADRestore


Contains details about the restore process for an Active Directory item.

VEADRestore

| Property | Type | Description |
| Id | GUID | Restore job ID. |
| Server | String? | DNS name or IP address of the target server. |
| TargetContainer | String? | Destination container. |
| Status | String | Status of the restore job operation. Possible values:   * Created * Initializing * Running * Success * Canceling * Canceled * Failed * WaitingForRetry * Completed |
| ExceptionMessage | String | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VEADItemRestore](start-veaditemrestore.md)
* [Get-VEADItemRestore](get-veaditemrestore.md)
* [Stop-VEADItemRestore](stop-veaditemrestore.md)

Page updated 2026-02-06

