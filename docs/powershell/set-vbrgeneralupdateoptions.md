---
title: "Set-VBRGeneralUpdateOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrgeneralupdateoptions.html"
last_updated: "2/13/2026"
product_version: "13.0.1.1071"
---

# Set-VBRGeneralUpdateOptions


Short Description

Modifies general update settings for the Linux-based backup server and Veeam Infrastructure Appliances.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGeneralUpdateOptions [-SourceRepositoryType <VBRUpdateSourceRepositoryType>] [-AutoUpdatePeriod <Int32>] [-CustomRepositoryPath <String>] [-ServerCertificate <X509Certificate2>] [-MaintenanceWindow <VBRMaintenanceWindowOptions>] [-UpdatesType <VBRUpdateType>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies general update settings for the Linux-based backup server and Veeam Infrastructure Appliances.

|  |
| --- |
| Important |
| Before you run this cmdlet, you must get the certificate either from a file or from the certificates store. |

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
| This command sets a local repository as the source of updates and specifies a maintenance window. Security and optional updates are installed. There is a 30 day compliance deadline.  |  | | --- | | $cert = New-SelfSignedCertificate -DnsName "yourserver.domain.com" -CertStoreLocation "Cert:\LocalMachine\My"  $thumbprint = $cert.Thumbprint  $store = New-Object System.Security.Cryptography.X509Certificates.X509Store("My", "LocalMachine")  $store.Open("ReadOnly")  $cert = $store.Certificates | Where-Object { $\_.Thumbprint -eq $thumbprint }  $store.Close()  $dailywindow = New-VBRDailyOptions  $maintenancewindow = New-VBRMaintenanceWindowOptions -Enable -DailyOptions $dailywindow  Set-VBRGeneralUpdateOptions -SourceRepositoryType "Custom" -AutoUpdatePeriod "30" -CustomRepositoryPath "https://repository.company.local/rocky/9.2" -ServerCertificate $cert -MaintenanceWindow $maintenancewindow -UpdatesType "SecurityAndOptional" |  Perform the following steps:   1. Run the [New-SelfSignedCertificate](https://learn.microsoft.com/en-us/powershell/module/pki/new-selfsignedcertificate?view=windowsserver2025-ps) cmdlet to create a self-signed certificate. Save the result to the $cert variable. 2. Commands up to $store.Close() are required to retrieve the certificate from the store by thumbprint. 3. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Save the result to the $dailywindow variable. 4. Run the [New-VBRMaintenanceWindowOptions](new-vbrmaintenancewindowoptions.md) cmdlet. Specify the Enable parameter. Set $dailywindow as the DailyOptions parameter value. 5. Run the Set-VBRGeneralUpdateOptions cmdlet and specify the following settings:  * Specify the SourceRepositoryType, AutoUpdatePeriod, CustomRepositoryPath and UpdatesType parameter values. * Set the $cert variable as the ServerCertificate parameter value. * Set the $maintenancewindow variable as the MaintenanceWindow parameter value. |

Related Commands

* [New-VBRMaintenanceWindowOptions](new-vbrmaintenancewindowoptions.md)
* [Get-VBRGeneralUpdateOptions](get-vbrgeneralupdateoptions.md)


