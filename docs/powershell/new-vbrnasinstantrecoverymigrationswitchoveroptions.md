---
title: "New-VBRNASInstantRecoveryMigrationSwitchOverOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnasinstantrecoverymigrationswitchoveroptions.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# New-VBRNASInstantRecoveryMigrationSwitchOverOptions


Short Description

Defines the switchover parameter that can be used when starting the file share migration session or for changing settings of an already running file share migration session.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define settings for performing a switchover in the automatic mode.

|  |
| --- |
| New-VBRNASInstantRecoveryMigrationSwitchOverOptions [-Auto]  [<CommonParameters>] |

* Define settings for performing a switchover in the manual mode.

|  |
| --- |
| New-VBRNASInstantRecoveryMigrationSwitchOverOptions [-Manual]  [<CommonParameters>] |

You can start a switchover in the manual mode by using the [Switch-VBRNASInstantRecoveryMigration](switch-vbrnasinstantrecoverymigration.md) cmdlet.

* Define settings for performing a switchover in the scheduled mode.

|  |
| --- |
| New-VBRNASInstantRecoveryMigrationSwitchOverOptions [-Scheduled] -SwitchingTimeUtc <DateTime>  [<CommonParameters>] |

Detailed Description

This cmdlet defines the switchover parameter that can be used when starting the file share migration session or for changing settings of an already running file share migration session. You can use this cmdlet to define settings for performing a switchover in the automatic, manual or scheduled mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Auto | Defines that the switchover will be performed in the Automatic mode. | SwitchParameter | True | Named | False |
| Manual | Defines that the switchover will be performed in the Manual mode.  Use the [Switch-VBRNASInstantRecoveryMigration](switch-vbrnasinstantrecoverymigration.md) cmdlet to start the switchover in the Manual mode. | SwitchParameter | True | Named | False |
| Scheduled | Defines that the switchover will be performed in the Scheduled mode. | SwitchParameter | True | Named | False |
| SwitchingTimeUtc | For the Scheduled switchover option, specifies data and time when the switchover will take place. | DateTime | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASInstantRecoveryMigrationSwitchOverOptions](vbrnasinstantrecoverymigrationswitchoveroptions.md) object that defines settings of the migration to production session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Automatic Switchover Options for Migration of Instant Restore for File Backups

|  |  |
| --- | --- |
| This command defines settings for performing a switchover in the automatic mode.  |  | | --- | | $switchover = New-VBRNASInstantRecoveryMigrationSwitchOverOptions -Auto  Write-Output "Create automatic options for migration of instant restore for file backups."  Write-Output $switchover | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Manual Switchover Options for Migration of Instant Restore for File Backups

|  |  |
| --- | --- |
| This command defines settings for performing a switchover in the manual mode.  |  | | --- | | $switchover = New-VBRNASInstantRecoveryMigrationSwitchOverOptions -Manual  Write-Output "Create manual options for migration of instant restore for file backups."  Write-Output $switchover | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Scheduled Switchover Options for Migration of Instant Restore for File Backups

|  |  |
| --- | --- |
| This command defines settings for performing a switchover in the scheduled mode.  |  | | --- | | $switchover = New-VBRNASInstantRecoveryMigrationSwitchOverOptions -Scheduled -SwitchingTimeUtc "2020-11-24 13:00:00"  Write-Output "Create scheduled options for migration of instant restore for file backups."  Write-Output $switchover | |

Related Commands

[Switch-VBRNASInstantRecoveryMigration](switch-vbrnasinstantrecoverymigration.md)


