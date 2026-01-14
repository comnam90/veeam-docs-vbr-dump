---
title: "Assign-VBRInstanceWorkload"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/assign-vbrinstanceworkload.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Assign-VBRInstanceWorkload

In this article

Short Description

Sets the product edition for standalone Veeam Agents.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Assign-VBRInstanceWorkload -Workload <VBRLicensedInstanceWorkload[]> -LicenseMode <VBRAgentLicenseMode> {Server | Workstation}  [<CommonParameters>] |

Detailed Description

This cmdlet sets the product edition for standalone Veeam Agents to one of the following:

* Server edition
* Workstation edition

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Workload | Specifies an array of protected workloads. The cmdlet will set the product edition for these workloads. | Accepts the [VBRLicensedInstanceWorkload](vbrlicensedinstanceworkload.md)[] object. To get this object, run the [Get-VBRLicensedInstanceWorkload](get-vbrlicensedinstanceworkload.md) cmdlet. | True | Named | False |
| LicenseMode | Specifies a product edition. The cmdlet will set this product edition to protected. You can specify either of the following product editions:   * Server * Workstation | [VBRAgentLicenseMode](enums.md#VBRAgentLicenseMode) | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Server Edition

|  |  |
| --- | --- |
| This example shows how to set the Server edition for a standalone Veeam Agent that is running the Workstation edition.  |  | | --- | | $license = Get-VBRInstalledLicense  $workload = Get-VBRLicensedInstanceWorkload -License $license  Assign-VBRInstanceWorkload -Workload $workload -LicenseMode Server |  Perform the following steps:   1. Run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. Save the result to the $license variable. 2. Run the [Get-VBRLicensedInstanceWorkload](get-vbrlicensedinstanceworkload.md) cmdlet. Set the $license variable as the License parameter value. Save the result to the $workload variable.  1. Run the Assign-VBRInstanceWorkload cmdlet. Set the $workload variable as the Workload parameter value. Set the Server option for the LicenseMode parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Workstation Edition

|  |  |
| --- | --- |
| This example shows how to set the Workstation edition for a standalone Veeam Agent that is running the Server edition.  |  | | --- | | $license = Get-VBRInstalledLicense  $workload = Get-VBRLicensedInstanceWorkload -License $license  Assign-VBRInstanceWorkload -Workload $workload -LicenseMode Workstation |  Perform the following steps:   1. Run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. Save the result to the $license variable. 2. Run the [Get-VBRLicensedSocketWorkload](get-vbrlicensedsocketworkload.md) cmdlet. Set the $license variable as the License parameter value. Save the result to the $workload variable. 3. Run the Assign-VBRInstanceWorkload cmdlet. Set the $workload variable as the Workload parameter value. Set the Workstation option for the LicenseMode parameter. |

Related Commands

* [Get-VBRInstalledLicense](get-vbrinstalledlicense.md)
* [Get-VBRLicensedSocketWorkload](get-vbrlicensedsocketworkload.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
