---
title: "Get-VBRBackupServerDeployerCertificate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackupserverdeployercertificate.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBRBackupServerDeployerCertificate

In this article

Short Description

Downloads Veeam Installer Service and Veeam Deployer Service certificates.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRBackupServerDeployerCertificate -ExportPath <String> [-AllPlatforms] [<CommonParameters>] |

Detailed Description

This cmdlet downloads Veeam Installer Service and Veeam Deployer Service certificates to the specified location.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ExportPath | Specifies a path to a location. The cmdlet will download the certificates to this location on the server where the cmdlet was executed. | String | True | Named | True (ByPropertyName, ByValue) |
| AllPlatforms | Specifies that the cmdlet will download certificates for both Microsoft Windows and Linux computers. If you run the cmdlet without this parameter, it will download certificates only for Linux computers. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Downloading Veeam Deployer Service Certificate to Certain Folder

|  |  |
| --- | --- |
| This command downloads the Veeam Deployer Service certificate to the "C:\Users\Administrator\Documents" folder.  |  | | --- | | Get-VBRBackupServerDeployerCertificate -ExportPath "C:\Users\Administrator\Documents" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Downloading Veeam Installer Service and Veeam Deployer Service Certificates to Certain Folder

|  |  |
| --- | --- |
| This command downloads the Veeam Installer Service and Veeam Deployer Service certificates to the "C:\Users\Administrator\Documents" folder.  |  | | --- | | Get-VBRBackupServerDeployerCertificate -ExportPath "C:\Users\Administrator\Documents" -AllPlatforms | |

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
