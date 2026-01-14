---
title: "New-VBRComputerWarningOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcomputerwarningoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# New-VBRComputerWarningOptions

In this article

Short Description

Defines notification settings for computers not processed by Veeam Agent jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRComputerWarningOptions [-Enable] [-WarningPolicy <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRComputerWarningOptions object. This object defines notification settings for computers not processed by Veeam Agent jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Enable | Defines that the notification for computers not processed by Veeam Agent jobs are enabled. If you want to disable these notifications, set this parameter to the $false value: Enable:$false.  Default: True. | SwitchParameter | False | Named | False |
| WarningPolicy | Specifies a number of days within which Veeam Agent must send notifications. When this period is exceeded, the cmdlet will send notifications if Veeam Agent job did not process machines within the specified period.  Permitted values: 1-999.  Default: 14 | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerWarningOptions object that defines notifications settings for computers not processed by Veeam Agent jobs.

Examples

Defining Notifications Settings for Computers not Processed by Veeam Agent Jobs

This command enables notification settings for computers not processed by Veeam Agent jobs.

|  |
| --- |
| $warning = New-VBRComputerWarningOptions -Enable |

Page updated 10/21/2024

Page content applies to build 13.0.1.1071
