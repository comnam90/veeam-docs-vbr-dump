---
title: "Get-VBRLicensedInstanceWorkload"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlicensedinstanceworkload.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRLicensedInstanceWorkload


Short Description

Returns details on protected workloads for the per-instance license.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRLicensedInstanceWorkload -License <VBRInstalledLicense>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRLicensedInstanceWorkload object that contains details on protected workloads for the per-instance license that Veeam Backup & Replication applies to back up these workloads.

|  |
| --- |
| Note |
| The cmdlet returns information on a number of processed workloads that consume instances from the license scope. Instances are not consumed if a provider obtains a rental license and workloads have been processed for the first time during the current month. These workloads are counted separately and the cmdlet will display them under the following tenant settings:   * NewVMBackupCount * NewWorkstationBackupCount * NewServerBackupCount * NewReplicaCount   Workloads that start to consume instances on the first day of the following month are displayed under the following tenant settings:   * VMBackupCount * WorkstationBackupCount * ServerBackupCount * ReplicaCount   If a tenant obtains a rental license, these workloads do not consume instances from the provider license scope and are displayed under the following tenant settings:   * RentalVMBackupCount * RentalWorkstationBackupCount * RentalServerBackupCount * RentalReplicaCount |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| License | Specifies a license. The cmdlet will return details on protected workloads that Veeam Backup & Replication backs up using this license. | Accepts the [VBRInstalledLicense](vbrinstalledlicense.md) object. To get this object, run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRLicensedInstanceWorkload](vbrlicensedinstanceworkload.md)

Examples

Getting Details on Protected Workloads

This example shows how to get details on protected workloads for the per-instance license that Veeam Backup & Replication applies to back up these workloads.

|  |
| --- |
| $license = Get-VBRInstalledLicense  Get-VBRLicensedInstanceWorkload -License $license |

Perform the following steps:

1. Run the [Get-VBRInstalledLicense](get-vbrinstalledlicense.md) cmdlet. Save the result to the $license variable.
2. Run the Get-VBRLicensedInstanceWorkload cmdlet. Set the $license variable as the License parameter value.

Related Commands

[Get-VBRInstalledLicense](get-vbrinstalledlicense.md)


