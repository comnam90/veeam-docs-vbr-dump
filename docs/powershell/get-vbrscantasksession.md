---
title: "Get-VBRScanTaskSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrscantasksession.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRScanTaskSession

In this article

Short Description

Returns scan task sessions performed during the specified SureBackup session.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRScanTaskSession -InitiatorSessionId <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns scan task sessions performed during the specified SureBackup session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InitiatorSessionId | Specifies the array of SureBackup task sessions IDs. The cmdlet will return task IDs performed during these sessions. | Accepts the VBRSureBackupTaskSession object. To get this object, run the [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupScanTaskSession object that contains scan tasks performed during the SureBackup session.

Examples

Getting List of SureBackup Scan Task Sessions

This example shows how to get the list of scan task sessions performed during the SureBackup job session with 8e3cf452-23cb-490a-a86a-f802940e26df ID.

|  |
| --- |
| $sbs = Get-VBRSureBackupSession -ID 8e3cf452-23cb-490a-a86a-f802940e26df  $ts = Get-VBRSureBackupTaskSession -Session $sbs  Get-VBRScanTaskSession -InitiatorSessionId $ts.id |

Perform the following steps:

1. Run the [Get-VBRSureBackupSession](get-vbrsurebackupsession.md) cmdlet. Specify the ID parameter. Save the result to the $sbs variable.
2. Run the [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md) cmdlet. Set the $sbs variable as the Session parameter value. Save the result to the $ts variable.
3. Run the Get-VBRScanTaskSession cmdlet. Set the $ts.id variable as the InitiatorSessionId parameter value.

Related Commands

* [Get-VBRSureBackupSession](get-vbrsurebackupsession.md)
* [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
