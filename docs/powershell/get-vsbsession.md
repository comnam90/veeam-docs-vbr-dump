---
title: "Get-VSBSession (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vsbsession.html"
last_updated: "2/26/2024"
product_version: "13.0.1.1071"
---

# Get-VSBSession (obsolete)


Short Description

Returns SureBackup sessions that have been run.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VSBSession [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of all SureBackup sessions that have been run.

Run the [Get-VSBTaskSession](get-vsbtasksession.md) cmdlet to get the list of all tasks performed during the specific SureBackup session.

Run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet to get list of backup sessions that have been run.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of SureBackup session names. The cmdlet will return sessions with these names.  The name of a SureBackup session is the name of the SureBackup job. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All SureBackup Sessions

|  |  |
| --- | --- |
| This command looks for the list of all SureBackup sessions.  |  | | --- | | Get-VSBSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All SureBackup Session for Selected Job

|  |  |
| --- | --- |
| This command looks for the Winserver SureJob SureBackup session.  |  | | --- | | Get-VSBSession -Name \*Winserver SureJob\* | |


