---
title: "Get-VBRNASInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasinstantrecoverymigration.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNASInstantRecoveryMigration


Short Description

Returns active sessions of migration to production during the instant file share recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return all active sessions of migration to production for NAS instant recovery.

|  |
| --- |
| Get-VBRNASInstantRecoveryMigration [-All]  [<CommonParameters>] |

* Return NAS instant recovery migration sessions by their IDs.

|  |
| --- |
| Get-VBRNASInstantRecoveryMigration [-Id <Guid[]>]  [<CommonParameters>] |

* Return NAS instant recovery migration session for a certain instant recovery session.

|  |
| --- |
| Get-VBRNASInstantRecoveryMigration [-InstantRecovery <VBRNASInstantRecovery[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns active sessions of migration to production during the instant file share recovery.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| All | Defines that the cmdlet will return all active sessions of migration to production for NAS instant recovery. | SwitchParameter | False | Named | False |
| Id | Specifies an array of IDs for migration sessions. The cmdlet will return sessions with these IDs.  If the session with the specified ID is not found, the cmdlet will return an error. | Guid[] | False | Named | True (ByPropertyName) |
| InstantRecovery | Specifies an array of instant recovery sessions with the started sessions of migration to production. | Accepts the [VBRNASInstantRecovery](vbrnasinstantrecovery.md)[] object. To get this object, run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASInstantRecoveryMigration](vbrnasinstantrecoverymigration.md) object that defines settings of the migration to production session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active Migration Sessions for Instant Restore for File Backup

|  |  |
| --- | --- |
| This example shows how to get all active migration sessions for instant restore for file backup sessions.  |  | | --- | | $migrations = Get-VBRNASInstantRecoveryMigration  Write-Output "Get migration sessions of instant restore for file backups."  Write-Output $migrations |  Perform the following steps:   1. Run the Get-VBRNASInstantRecoveryMigration cmdlet. Save the result to the $migrations variable. 2. Run the Write-Output cmdlet. Specify the output wording. 3. Run the Write-Output cmdlet. Provide the $migrations variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Migration Sessios for Instant Restore for File Backup by IDs

|  |  |
| --- | --- |
| This example shows how to get migration to production sessions with certain IDs.  |  | | --- | | $migrations = Get-VBRNASInstantRecoveryMigration -Id ("49664A5F-9C55-4A1F-8E6A-1CD5705A684B", "42696B53-6FEC-4148-9354-AA9E4B52DED9")  Write-Output "Get migration sessions of instant restore for file backups."  Write-Output $migrations |  Perform the following steps:   1. Run the Get-VBRNASInstantRecoveryMigration cmdlet. Save the result to the $migrations variable. 2. Run the Write-Output cmdlet. Specify the output wording. 3. Run the Write-Output cmdlet. Provide the $migrations variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Migration Sessions for Specified Instant Restore for File Backups Sessions

|  |  |
| --- | --- |
| This example shows how to get migration to production sessions for certain instant restore sessions.  |  | | --- | | $nasInstantRecoveries = Get-VBRNASInstantRecovery  $migrations = Get-VBRNASInstantRecoveryMigration -InstantRecovery $nasInstantRecoveries  Write-Output "Get migration sessions of instant restore for file backups."  Write-Output $migrations |  Perform the following steps:   1. Run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. Save the result to the $nasInstantRecoveries variable. 2. Run the Get-VBRNASInstantRecoveryMigration cmdlet. Set the $nasInstantRecoveries variable as the InstantRecovery parameter value. 3. Run the Write-Output cmdlet. Specify the output wording. 4. Run the Write-Output cmdlet. Provide the $migrations variable. |

Related Commands

[Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md)


