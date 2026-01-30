---
title: "New-VBRMaintenanceWindowOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmaintenancewindowoptions.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# New-VBRMaintenanceWindowOptions


Short Description

Configures a maintenance window for automatic update installation.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMaintenanceWindowOptions [-Enable] [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRMaintenanceWindowOptions object. This object contains the settings of a maintenance window.

Run the [Set-VBRGeneralUpdateOptions](set-vbrgeneralupdateoptions.md) cmdlet to apply the settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DailyOptions | Specifies a day of the week when updates are installed automatically. | Accepts the VBRDailyOptions object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| Enable | Enables a maintenance window when updates are installed automatically. | SwitchParameter | False | Named | False |
| MonthlyOptions | Specifies a day of the month when updates are installed automatically. | Accepts the VBRMonthlyOptions object. To get this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRMaintenanceWindowOptions

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Weekly Maintenance Window

|  |  |
| --- | --- |
| This command creates a maintenance window on a specific day of the week.  |  | | --- | | $dailywindow = [New-VBRDailyOptions](new-vbrdailyoptions.md)  New-VBRMaintenanceWindowOptions -Enable -DailyOptions $dailywindow |  Perform the following steps:   1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Save the result to the $dailywindow variable. 2. Run the New-VBRMaintenanceWindowOptions cmdlet. Specify the Enable parameter value. Set the $dailywindow variable as the DailyOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Monthly Maintenance Window

|  |  |
| --- | --- |
| This command creates a maintenance window on a specific date of the month.  |  | | --- | | $monthlywindow = [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)  New-VBRMaintenanceWindowOptions -Enable -MonthlyOptions $monthlywindow |  Perform the following steps:   1. Run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. Save the result to the $monthlywindow variable. 2. Run the New-VBRMaintenanceWindowOptions cmdlet. Specify the Enable parameter value. Set the $monthlywindow variable as the MonthlyOptions parameter value. |

Related Commands

[Set-VBRGeneralUpdateOptions](set-vbrgeneralupdateoptions.md)


