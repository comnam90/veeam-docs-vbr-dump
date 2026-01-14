---
title: "Set-VBRComputerGFSYearlyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputergfsyearlyoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerGFSYearlyOptions

In this article

Short Description

Modifies settings of for the yearly GFS retention policy for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerGFSYearlyOptions -Options <VBRComputerGFSYearlyOptions> [-RetentionPeriod <Int32>] [-SelectedMonth <VBRMonth>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the yearly GFS retention policy that you can apply to Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies a yearly GFS retention policy for Veeam Agent backup jobs. The cmdlet will modify this policy. | Accepts the VBRComputerGFSYearlyOptions object. To create this object, run the [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md) cmdlet | True | Named | True |
| RetentionPeriod | Specifies the number of months to keep yearly full backups. | Int32 | False | Named | False |
| SelectedMonth | Specifies a month when a yearly backup is created. You can specify either of the following months:   * January * February * March * April * May * June * July * August * September * October * November * December | VBRMonth | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSYearlyOptions object that contains settings of the yearly GFS retention policy that you can apply to Veeam Agent backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Number of Years for GFS Retention Policy

|  |  |
| --- | --- |
| This example shows how to modify the settings of the yearly GFS retention policy and change a number of years to keep yearly backups. With these settings applied, Veeam Backup & Replication will keep yearly backups for 3 years.  |  | | --- | | $options = New-VBRComputerGFSYearlyOptions -RetentionPeriod 2 -SelectedMonth November  Set-VBRComputerGFSYearlyOptions -Options $options -RetentionPeriod 3 |  Perform the following steps:   1. Run the [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedWeek parameter values. Save the result to the $options variable. 2. Run the Set-VBRComputerGFSYearlyOptions cmdlet. Set the $options variable as the Options parameter value. Specify the RetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Month of Yearly Backup Schedule

|  |  |
| --- | --- |
| This example shows how to modify the settings of the yearly GFS retention policy and change a month when a yearly backup is created. With these settings applied, Veeam Backup & Replication will create yearly backups in February.  |  | | --- | | $options = New-VBRComputerGFSYearlyOptions -RetentionPeriod 2 -SelectedMonth November  Set-VBRComputerGFSYearlyOptions -Options $options -SelectedMonth February |  Perform the following steps:   1. Run the [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedMonth parameter values. Save the result to the $options variable. 2. Run the Set-VBRComputerGFSYearlyOptions cmdlet. Set the $options variable as the Options parameter value. Set the February option for the SelectedMonth parameter. |

Related Commands

[New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md)

Page updated 10/21/2024

Page content applies to build 13.0.1.1071
