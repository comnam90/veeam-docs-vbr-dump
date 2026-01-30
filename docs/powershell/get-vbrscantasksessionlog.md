---
title: "Get-VBRScanTaskSessionLog"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrscantasksessionlog.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRScanTaskSessionLog


Short Description

Returns the results of scan task sessions performed during the specified SureBackup job session.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRScanTaskSessionLog -ScanTaskSession <VBRScanTaskSession>  [<CommonParameters>] |

Detailed Description

Returns the results of scan task sessions performed during the specified SureBackup job session. The results are written in .txt log files.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ScanTaskSession | Specifies the array of scan task sessions performed during the specified SureBackup session. The cmdlet will return scan task sessions performed during this SureBackup session. | Accepts the VBRSureBackupScanTaskSession object. To get this object, run the [Get-VBRScanTaskSession](get-vbrscantasksession.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupScanTaskSessionLog object that contains the results of scan tasks performed during the SureBackup job session.

Examples

Getting List of SureBackup Scan Task Sessions Results

This example shows how to get the list of scan task sessions results performed during the SureBackup job session with 8e3cf452-23cb-490a-a86a-f802940e26df ID.

|  |
| --- |
| $sbs = Get-VBRSureBackupSession -ID 8e3cf452-23cb-490a-a86a-f802940e26df  $ts = Get-VBRSureBackupTaskSession -Session $sbs  $sts = Get-VBRScanTaskSession -InitiatorSessionId $ts.id  Get-VBRScanTaskSessionLog -ScanTaskSession $sts |

Perform the following steps:

1. Run the [Get-VBRSureBackupSession](get-vbrsurebackupsession.md) cmdlet. Specify the ID parameter. Save the result to the $sbs variable.
2. Run the [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md) cmdlet. Set the $sbs variable as the Session parameter value. Save the result to the $ts variable.
3. Run the [Get-VBRScanTaskSession](get-vbrscantasksession.md) cmdlet. Set the $ts.id variable as the InitiatorSessionId parameter value. Save the result to the $sts variable.
4. Run the Get-VBRScanTaskSessionLog cmdlet. Set the $sts variable as the ScanTaskSession parameter value.

Related Commands

* [Get-VBRSureBackupSession](get-vbrsurebackupsession.md)
* [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md)
* [Get-VBRScanTaskSession](get-vbrscantasksession.md)


