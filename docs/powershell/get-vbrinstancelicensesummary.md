---
title: "Get-VBRInstanceLicenseSummary"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrinstancelicensesummary.html"
last_updated: "12/9/2024"
product_version: "13.0.1.1071"
---

# Get-VBRInstanceLicenseSummary


Short Description

Returns details on the per-instance license usage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRInstanceLicenseSummary -License <VBRInstalledLicense>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRInstanceLicenseSummary object that contains details on the per-instance license usage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| License | Specifies a license. The cmdlet will return details on the per-instance license usage for this license. | Accepts the VBRInstalledLicense object. To get this object, run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRInstanceLicenseSummary](vbrinstancelicensesummary.md)

Examples

Getting Details on Per-Instance License

This example shows how to get details on the per-instance license usage.

|  |
| --- |
| $license = Get-VBRInstalledLicense  Get-VBRInstanceLicenseSummary -License $license  LicensedInstancesNumber : 1000  UsedInstancesNumber     : 2  NewInstancesNumber      : 0  RentalInstancesNumber   : 0  Object                  : {Veeam.Backup.PowerShell.Infos.VBRInstanceLicenseSummaryObject}  Workload                : {BackupServer01, SQLServer05} |

Perform the following steps:

1. Run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. Save the result to the $license variable.
2. Run the Get-VBRInstanceLicenseSummary cmdlet. Set the $license variable as the License parameter value.

The cmdlet output will contain the following details on the per-instance license usage: LicensedInstancesNumber, UsedInstancesNumber, NewInstancesNumber, RentalInstancesNumber, Object and Workload.

Related Commands

[Get-VBRInstalledLicense](get-vbrinstalledlicense.md)


