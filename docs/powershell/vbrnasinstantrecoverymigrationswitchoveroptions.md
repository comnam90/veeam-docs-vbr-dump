---
title: "VBRNASInstantRecoveryMigrationSwitchOverOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasinstantrecoverymigrationswitchoveroptions.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRNASInstantRecoveryMigrationSwitchOverOptions


Contains the switchover options with the specified parameters.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Type | VBRNASInstantRecoveryMigrationSwitchOverType | Selected switchover mode:   * Auto * Manual * Scheduled |
| SwitchingTimeUtc | DateTime | Date and time to perform the switchover. Corresponds to the SwitchingTimeUtc parameter if you selected the Scheduled mode. Otherwise is Null. |

Related Commands

[New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md)


