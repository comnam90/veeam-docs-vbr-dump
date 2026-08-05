---
title: "VEADExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veadexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VEADExport


Contains details about the export process for an Active Directory item.

VEADExport

| Property | Type | Description |
| JobId | GUID | Job ID. |
| Status | String | Status of the export operation. Possible values:   * Created * Initializing * Running * Success * Canceling * Canceled * Failed * WaitingForRetry * Completed |
| ExceptionMessage | String | Error or warning message triggered by unexpected conditions during restore. |
| ExportPath | String | Destination path for the Active Directory object or container. |

Related Commands

* [Start-VEADItemExport](start-veaditemexport.md)
* [Get-VEADItemExport](get-veaditemexport.md)
* [Stop-VEADItemExport](stop-veaditemexport.md)

Page updated 2026-01-30

