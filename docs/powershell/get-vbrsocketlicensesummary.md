---
title: "Get-VBRSocketLicenseSummary"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsocketlicensesummary.html"
last_updated: "12/9/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSocketLicenseSummary


Short Description

Returns details on the per-socket license usage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSocketLicenseSummary -License <VBRInstalledLicense>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the [VBRSocketLicenseSummary](vbrsocketlicensesummary.md) object that contains details on the per-socket license usage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| License | Specifies a license. The cmdlet will return details on the per-socket license usage for this license. | Accepts the [VBRInstalledLicense](vbrinstalledlicense.md) object. To get this object, run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSocketLicenseSummary](vbrsocketlicensesummary.md)

Examples

Getting Details on Per-Socket License

This example shows how to get details on the per-socket license usage.

|  |
| --- |
| $license = Get-VBRInstalledLicense  Get-VBRSocketLicenseSummary -License $license         LicensedSocketsNumber             UsedSocketsNumber        RemainingSocketsNumber Workload         ---------------------             -----------------        ---------------------- --------                            50                             2                            48 {Microsoft Hyper-V}                            75                            10                            65 {VMware vSphere}                            30                            25                             5 {Nutanix AHV} |

Perform the following steps:

1. Run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. Save the result to the $license variable.
2. Run the Get-VBRSocketLicenseSummary cmdlet. Set the $license variable as the License parameter value.

The cmdlet output will contain the following details on the per-socket license usage: LicensedSocketsNumber, UsedSocketsNumber, RemainingSocketsNumber and Workload.

Related Commands

[Get-VBRInstalledLicense](get-vbrinstalledlicense.md)


