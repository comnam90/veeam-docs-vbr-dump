---
title: "VBRAzureInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazureinstantrecovery.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# VBRAzureInstantRecovery


Contains an object with information on Instant Recovery to Microsoft Azure.

Properties

| Property | Type | Description |
| --- | --- | --- |
| RestorePointId | Guid | A restore point ID. |
| Platform | [VBRPlatform](enums.md#vbrplatform) | A platform where the recovered workload resides. |
| State | VBRAzureInstantRecoveryState | A recovery state. |
| TargetVm | [VBRAzureIRTargetVmInfo](vbrazureirtargetvminfo.md) | Information on a Microsoft Azure VM. |
| Log | VBRLogItem[] | Instant Recovery to Microsoft Azure session logs. |

Related Commands

* [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md)
* [Start-VBRAzureInstantRecoveryMigration](start-vbrazureinstantrecoverymigration.md)


