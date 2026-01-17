---
title: "Deprecated Cmdlets"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/deprecated_cmdlets_13.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Deprecated Cmdlets


This section contains information on Veeam Explorers PowerShell cmdlets that became deprecated in Veeam Backup & Replication 13.

Veeam Explorer for SAP HANA

In this version, some cmdlets in the Veeam Explorer for SAP HANA PowerShell module became deprecated. The cmdlets still work (as aliases of the new cmdlets, with identical functionality), but they may be removed in a future version. Use the new cmdlets instead.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Deprecated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | New Cmdlet | | --- | --- | | Restore-VEHANADatabase | [Start-VEHANADatabaseRestore](start-vehanadatabaserestore.md) | | Get-VEHANARestoreJob | [Get-VEHANADatabaseRestore](get-vehanadatabaserestore.md) | | Stop-VEHANARestoreJob | [Stop-VEHANADatabaseRestore](stop-vehanadatabaserestore.md) | |

Veeam Explorer for MongoDB

In Veeam Backup & Replication 13, some cmdlets in the Veeam Explorer for MongoDB PowerShell module became deprecated. The cmdlets still work (as aliases of the new cmdlets, with identical functionality), but they may be removed in a future version. Use the new cmdlets instead.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Deprecated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | New Cmdlet | | --- | --- | | Start-VEMDBRestoreJob | [Start-VEMDBDataRestore](start-vemdbdatarestore.md) | | Get-VEMDBRestoreJob | [Get-VEMDBDataRestore](get-vemdbdatarestore.md) | | Stop-VEMDBRestoreJob | [Stop-VEMDBDataRestore](stop-vemdbdatarestore.md) | |


