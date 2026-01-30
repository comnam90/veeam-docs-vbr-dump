---
title: "Get-VBRInstalledLicense"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrinstalledlicense.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRInstalledLicense


Short Description

Returns details about licenses installed on a backup server.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRInstalledLicense  [<CommonParameters>] |

Detailed Description

This cmdlet returns details about licenses installed on a backup server.

For more information on the license report, see the [Viewing License Information](https://helpcenter.veeam.com/docs/vbr/userguide/license_view.html?ver=13) section of User Guide for VMware vSphere.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRInstalledLicense](vbrinstalledlicense.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Details About License

|  |  |
| --- | --- |
| This command returns details about a license installed on a backup server.  |  | | --- | | Get-VBRInstalledLicense | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Details About Licensed CPU Sockets

|  |  |
| --- | --- |
| This example shows how to get details about a number of licensed CPU sockets on protected Microsoft Hyper-V hosts and VMware ESXi hosts.  |  | | --- | | $license = Get-VBRInstalledLicense  $license.SocketLicenseSummary  LicensedSocketsNumber UsedSocketsNumber RemainingSocketsNumber     Type  --------------------- ----------------- ----------------------     ----                     3                 2                     15   HyperV                     2                 1                     20  vSphere |  Perform the following steps:   1. Run the Get-VBRInstalledLicense cmdlet. Save the result to the $license variable. 2. Get the SocketLicenseSummary property of the $license variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Details About Available Licenses

|  |  |
| --- | --- |
| This example shows how to get details about a number of available instances.  |  | | --- | | $license =  Get-VBRInstalledLicense  $license.InstanceLicenseSummary  LicensedInstancesNumber : 1000  UsedInstancesNumber     : 2  NewInstancesNumber      : 0  RentalInstancesNumber   : 0  Object                  : {Veeam.Backup.PowerShell.Infos.VBRInstanceLicenseSummaryObject}  Workload                : {srv009, SQLsrv} |  Perform the following steps:   1. Run the Get-VBRInstalledLicense cmdlet. Save the result to the $license variable. 2. Get the InstanceLicenseSummary property of the $license variable. |


