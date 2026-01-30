---
title: "VBRFullBackupToTapePolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrfullbackuptotapepolicy.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRFullBackupToTapePolicy


Contains virtual full schedule.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Type | [VBRFullBackupToTapePolicyType](enums.md#VBRFullBackupToTapePolicyType) | The type of the virtual full backups creation policy. |
| WeeklyOnDays | DayOfWeek[] | The days on which the synthesized full backups for tapes are created. |
| MonthlyOptions | [VBRMonthlyOptions](vbrmonthlyoptions.md) | Job monthly schedule settings. |

Related Commands

[New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md)


