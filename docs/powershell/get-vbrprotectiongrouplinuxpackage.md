---
title: "Get-VBRProtectionGroupLinuxPackage"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrprotectiongrouplinuxpackage.html"
last_updated: "4/15/2024"
product_version: "13.0.1.1071"
---

# Get-VBRProtectionGroupLinuxPackage


Short Description

Returns Veeam Agent for Linux packages.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRProtectionGroupLinuxPackage [-Name <String>] [-LinuxDistributionName <String[]>] [-LinuxPackageBitness <EOSPlatform>] [-Type <VBRLinuxAgentPackageType>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Veeam Agent for Linux packages.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LinuxDistributionName | Specifies an array of Veeam Agent for Linux packages that you specify for this parameter. The cmdlet will return Linux packages with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a name of the Veeam Agent for a Linux package. The cmdlet will return Linux packages with this name. | String | False | Named | True (ByValue, ByPropertyName) |
| LinuxPackageBitness | Specifies an operating system version of Veeam Agent for Linux packages. You can specify one of the following types of operating systems:   * X86 * X64 * Unknown | EOSPlatform | False | Named | True (ByValue, ByPropertyName) |
| Type | Specifies one of the following Linux packages type:   * Standard * Nosnap | [VBRLinuxAgentPackageType](enums.md#VBRLinuxAgentPackageType) | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRProtectionGroupLinuxPackage](vbrprotectiongrouplinuxpackage.md) object that contains Veeam Agent for Linux packages.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Veeam Agent for Linux Packages

|  |  |
| --- | --- |
| This command returns an array of all Veeam Agent for Linux packages.  |  | | --- | | Get-VBRProtectionGroupLinuxPackage | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Veeam Agent for Linux Packages

|  |  |
| --- | --- |
| This command returns an array of Debian and Ubuntu packages with the X64 operating system version.  |  | | --- | | Get-VBRProtectionGroupLinuxPackage -LinuxDistributionName "debian", "ubuntu" -LinuxPackageBitness X64 | |


