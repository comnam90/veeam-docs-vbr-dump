---
title: "Get-VBRSureBackupTaskSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsurebackuptasksession.html"
last_updated: "6/16/2025"
product_version: "13.0.1.1071"
---

# Get-VBRSureBackupTaskSession


Short Description

Returns tasks performed during the specified SureBackup session.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSureBackupTaskSession -Session <VBRSureBackupSession> [-Name <string[]>] [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of tasks performed during the specified SureBackup session.

Run the [Get-VBRTaskSession](get-vbrtasksession.md) cmdlet to get the tasks for backup, replication and backup copy sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the array of SureBackup sessions. The cmdlet will return tasks performed during these sessions. | Accepts the VBRSureBackupSession object. To get this object, run the [Get-VBRSureBackupSession](get-vbrsurebackupsession.md) cmdlet. | True | 0 | True (ByValue, |
| Name | Specifies the array of SureBackup job names. The cmdlet will return tasks performed for VMs in these jobs during the selected job session. | string[] | False | Named | True (ByValue, ByProperty Name) |
| ID | Specifies the array of SureBackup sessions ID. The cmdlet will return sessions with this ID. | guid[] | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupTaskSession object that contains settings of tasks performed during the SureBackup session.

Examples

Getting List of SureBackup Sessions by Name

This example shows how to get the list of tasks performed for the VM named srv1 in the SureBackup job session named Winserver SureBackupJob.

|  |
| --- |
| $job = Get-VBRSureBackupSession -Name "Winserver SureBackupJob"  Get-VBRSureBackupTaskSession -Session $job -Name "srv1" |

Perform the following steps:

1. Run the [Get-VBRSureBackupSession](get-vbrsurebackupsession.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Get-VBRSureBackupTaskSession cmdlet. Set the $job variable as the Session parameter value. Specify the Name parameter value.

Related Commands

[Get-VBRSureBackupSession](get-vbrsurebackupsession.md)


