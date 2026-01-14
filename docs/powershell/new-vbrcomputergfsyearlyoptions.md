---
title: "New-VBRComputerGFSYearlyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcomputergfsyearlyoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# New-VBRComputerGFSYearlyOptions

In this article

Short Description

Defines settings of the yearly GFS retention policy for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRComputerGFSYearlyOptions [-RetentionPeriod <Int32>] [-SelectedMonth <VBRMonth>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRComputerGFSMonthlyOptions object. This object contains settings of the yearly GFS retention policy that you can apply to Veeam Agent backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RetentionPeriod | Specifies the number of years to keep yearly full backups. | Int32 | False | Named | False |
| SelectedMonth | Specifies a month when a yearly backup is created. You can specify either of the following months:   * January * February * March * April * May * June * July * August * September * October * November * December | VBRMonth | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSYearlyOptions object that contains settings of the yearly GFS retention policy that you can apply to Veeam Agent backup jobs.

Examples

Defining Yearly GFS Retention Policy

This command defines a yearly GFS retention policy with the following settings:

* With these settings applied, Veeam Backup & Replication will keep yearly full backups for 2 years.
* With these settings applied, Veeam Backup & Replication will create yearly backups on November.

|  |
| --- |
| New-VBRComputerGFSYearlyOptions -RetentionPeriod 2 -SelectedMonth November |

Page updated 10/21/2024

Page content applies to build 13.0.1.1071
