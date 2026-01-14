---
title: "Set-VBRGeneralUpdateOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrgeneralupdateoptions.html"
last_updated: "9/8/2025"
product_version: "13.0.1.1071"
---

# Set-VBRGeneralUpdateOptions

In this article

Short Description

Modifies general update settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGeneralUpdateOptions [-SourceRepositoryType <VBRUpdateSourceRepositoryType>] [-AutoUpdatePeriod <Int32>] [-CustomRepositoryPath <String>] [-ServerCertificate <X509Certificate2>] [-MaintenanceWindow <VBRMaintenanceWindowOptions>] [-UpdatesType <VBRUpdateType>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies general update settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AutoUpdatePeriod | Specifies a compliance deadline for updates.  After being available for the specified number of days, any pending updates will be installed immediately. | Int32 | False | Named | False |
| CustomRepositoryPath | Specifies a local mirror of the Veeam update repository. | String | False | Named | False |
| MaintenanceWindow | Specifies a maintenance window when updates are installed automatically. | Accepts the VBRMaintenanceWindowOptions object. To get this object, run the [New-VBRMaintenanceWindowOptions](new-vbrmaintenancewindowoptions.md) cmdlet. | False | Named | False |
| ServerCertificate | Specifies the server certificate used during SSL verification. | X509Certificate2 | False | Named | False |
| SourceRepositoryType | Specifies if updates are installed from the official Veeam repository or a local mirror.   * Official — use this option to install updates from Veeam update repository. * Custom — use this option to install updates from the local mirror of Veeam update repository. | [VBRUpdateSourceRepositoryType](enums.md#VBRUpdateSourceRepositoryType) | False | Named | False |
| UpdatesType | Specifies if available optional updates are installed automatically. | VBRUpdateType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRGeneralUpdateOptions

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Updating From Veeam Repository

|  |  |
| --- | --- |
| This command sets the official Veeam repository as the source of updates and specifies a maintenance window. Only security updates are installed. There is a 30 day compliance deadline.  |  | | --- | | Set-VBRGeneralUpdateOptions -SourceRepositoryType "Official" -AutoUpdatePeriod "30" -MaintenanceWindow $maintenancewindow -UpdatesType "SecurityOnly" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Updating From Local Repository

|  |  |
| --- | --- |
| This command sets a local repository as the source of updates and specifies a maintenance window. Security and optional updates are installed. There is a 30 day compliance deadline.  |  | | --- | | Set-VBRGeneralUpdateOptions -SourceRepositoryType "Custom" -AutoUpdatePeriod "30" -CustomRepositoryPath "https://repository.company.local/rocky/9.2" -ServerCertificate $ServerCertificate -MaintenanceWindow $maintenancewindow -UpdatesType "SecurityAndOptional" | |

Related Commands

* [New-VBRMaintenanceWindowOptions](new-vbrmaintenancewindowoptions.md)
* [Get-VBRGeneralUpdateOptions](get-vbrgeneralupdateoptions.md)

Page updated 9/8/2025

Page content applies to build 13.0.1.1071
