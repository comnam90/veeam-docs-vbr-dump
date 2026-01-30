---
title: "Export-VBRRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrrestorepoint.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Export-VBRRestorePoint


Short Description

Exports backup files of a specific restore point.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRRestorePoint -RestorePoint <COib> [-RetentionPeriod <VBRExportRetentionPeriod>] [-RetentionNumber <Int32>] [-RetentionPeriodType <VBRRetentionPeriodType>] [-Reason <String>] [-Repository <CBackupRepository>]  [<CommonParameters>] |

Detailed Description

This cmdlet exports backup files of a specific restore point.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point. The cmdlet will export backup files of this restore point. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| RetentionPeriod | Specifies a retention period of exported backup files. The cmdlet will delete exported backup files within one of the following retention periods:   * Never * In1Month * In3Months * In6Months * In1Year * In2Years * In3Years * In5Years   Note: Use this parameter if the RetentionPeriodType and RetentionNumber parameters are not specified. | [VBRExportRetentionPeriod](enums.md#VBRExportRetentionPeriod) | False | Named | False |
| RetentionPeriodType | Specifies the type of the retention policy. You can set the following types:   1. Days: use this option if you want Veeam Backup & Replication to apply retention policy daily. 2. Months: use this option if you want Veeam Backup & Replication to apply retention policy monthly. 3. Years: use this option if you want Veeam Backup & Replication to apply retention policy yearly.   Use the RetentionNumber to specify the number of days, months or years.  Note: Use this parameter if the RetentionPeriod parameter is not specified. | VBRExportRetentionPeriod | False | Named | False |
| RetentionNumber | For the RetentionPeriodType option.  Specifies the period of time to keep the exported data. After this period finishes, Veeam Backup & Replication will remove data. | Int32 | False | Named | False |
| Reason | Specifies the reason of the export. | String | False | Named | False |
| Repository | Specifies the repository to which you want to export the restore point. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Exporting Backup Files of Specific Restore Point

This example shows how to export backup files of a specific restore point.

|  |
| --- |
| $restorepoint = Get-VBRRestorePoint  Export-VBRRestorePoint -RestorePoint $restorepoint[2] |

Perform the following steps:

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable.
2. Run the Export-VBRRestorePoint cmdlet. Set the third $restorepoint as the RestorePoint parameter value.

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


