---
title: "Get-VBRLicensedSocketWorkload"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlicensedsocketworkload.html"
last_updated: "12/9/2024"
product_version: "13.0.1.1071"
---

# Get-VBRLicensedSocketWorkload


Short Description

Returns details on licensed hosts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRLicensedSocketWorkload -License <VBRInstalledLicense>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRLicensedSocketWorkload object that contains details on licensed hosts for the per-socket license that Veeam Backup & Replication applies to back up these hosts.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| License | Specifies a license. The cmdlet will return details on licensed hosts that Veeam Backup & Replication backs up using this license. | Accepts the VBRInstalledLicense object. To get this object, run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRLicensedSocketWorkload](vbrlicensedsocketworkload.md)

Examples

Getting Details on Licensed Hosts

This example shows how to get details on licensed hosts for the per-socket license that Veeam Backup & Replication applies to back up these hosts.

|  |
| --- |
| $license = Get-VBRInstalledLicense  Get-VBRLicensedSocketWorkload -License $license |

Perform the following steps:

1. Run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. Save the result to the $license variable.
2. Run the Get-VBRLicensedSocketWorkload cmdlet. Set the $license variable as the License parameter value.

Related Commands

[Get-VBRInstalledLicense](get-vbrinstalledlicense.md)


