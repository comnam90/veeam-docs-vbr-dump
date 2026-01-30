---
title: "Export-VBRAudit"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbraudit.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Export-VBRAudit


Short Description

Exports report on actions performed in Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRAudit -From <datetime> -To <datetime> -FileFullPath <string>  [<CommonParameters>] |

Detailed Description

This cmdlet exports report that contain information on actions performed by an administrator in Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| From | Specifies the starting date of the report period. The cmdlet will generate a report starting from the specified date. | Accepts the DateTime object. To create this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | True | Named | False |
| To | Specifies the end date of the report period. The cmdlet will generate a report for a period ending on the specified date. | Accepts the DateTime object. To create this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | True | Named | False |
| FileFullPath | Specifies the name of the file and the target path where this file is located. This cmdlet will export the report to this file located in the specified destination. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAudit object that contains details on the exported report on actions performed by an administrator in Veeam Backup & Replication.

Examples

Exporting Report on Actions Performed in Veeam Backup & Replication

This example shows how to export a  report that contains information on actions performed by an administrator in Veeam Backup & Replication for the period from 02/02/2023 to 03/04/2023.

|  |
| --- |
| $fromdate = Get-Date -Year 2023 -Month 2 -Day 2 -Hour 0 -Minute 0 -Second 0  $todate = Get-Date -Year 2023 -Month 3 -Day 4 -Hour 0 -Minute 0 -Second 0  Export-VBRAudit -From $fromdate -To $todate -FileFullPath "C:\Reports\02-03.2021AuditReport.txt" |

Perform the following steps:

1. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $fromdate variable.
2. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $todate variable.
3. Run the Export-VBRAudit cmdlet. Specify the following settings:

* Set the $fromdate variable as the From parameter value.
* Set the $todate variable as the To parameter value.
* Specify the FileFullPath parameter value.

Related Commands

[Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


