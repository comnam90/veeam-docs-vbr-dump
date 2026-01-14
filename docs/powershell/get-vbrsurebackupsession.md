---
title: "Get-VBRSureBackupSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsurebackupsession.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSureBackupSession

In this article

Short Description

Returns SureBackup sessions that have been run.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSureBackupSession [-Name <string[]>] [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of all SureBackup sessions that have been run.

Run the [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md) cmdlet to get the list of all tasks performed during the specific SureBackup session.

Run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet to get list of backup sessions that have been run.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of SureBackup session names. The cmdlet will return sessions with these names.  The name of a SureBackup session is the name of the SureBackup job. | string[] | False | Named | True (ByValue, |
| ID | Specifies the array of SureBackup sessions IDs. The cmdlet will return sessions with these IDs. | guid[] | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupSession object that contains settings of SureBackup sessions.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of All SureBackup Sessions

|  |  |
| --- | --- |
| This command returns the list of all SureBackup sessions.  |  | | --- | | Get-VBRSureBackupSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting SureBackup Session by Name

|  |  |
| --- | --- |
| This command returns the SureBackup sessions named Winserver SureBackupJob.  |  | | --- | | Get-VBRSureBackupSession -Name "Winserver SureBackupJob" | |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
