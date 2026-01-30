---
title: "Generate-VBRBackupServerDeployerKit"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/generate-vbrbackupserverdeployerkit.html"
last_updated: "8/6/2025"
product_version: "13.0.1.1071"
---

# Generate-VBRBackupServerDeployerKit


Short Description

Generates Veeam Installer Service and Veeam Deployer Service certificates and installation packages for Microsoft Windows and Linux computers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Generate-VBRBackupServerDeployerKit [-ValidityPeriodInHours <Int32>] -ExportPath <String> [-AllPlatforms] [<CommonParameters>] |

Detailed Description

The cmdlet generates Veeam Installer Service and Veeam Deployer Service certificates and installation packages for Microsoft Windows and Linux computers and exports them to the specified location.

|  |
| --- |
| Important |
| Keep in mind that once you generate new setup files, any previously generated files will become obsolete. If you need to download existing setup files, use the [Get-VBRBackupServerDeployerCertificate](get-vbrbackupserverdeployercertificate.md) cmdlet. |

For more information, see the [Deploying Veeam Agents Using Veeam Deployment Kit](https://helpcenter.veeam.com/docs/vbr/userguide/agents_deploy_deployer.html?ver=13) section in the Veeam Backup & Replication User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ExportPath | Specifies a path to a location. The cmdlet will export generated files to this location on the server where the cmdlet was executed. | String | True | Named | True (ByPropertyName, ByValue) |
| ValidityPeriodInHours | Specifies a period in hours during the certificates are valid.  Permitted values: 1-8760.  Default: 720. | Int32 | False | Named | True (ByPropertyName, ByValue) |
| AllPlatforms | Specifies that the cmdlet will export installation packages for both Microsoft Windows and Linux computers. If you run the cmdlet without this parameter, it will export installation packages only for Linux computers. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Generating Veeam Deployer Service Certificate and Installation Packages for Linux Computers

|  |  |
| --- | --- |
| This command generates Veeam Deployer Service certificate and installation packages for Linux computers to the C:\Users\Administrator\Documents folder.  |  | | --- | | Generate-VBRBackupServerDeployerKit -ExportPath "C:\Users\Administrator\Documents" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Generating Veeam Deployer Service Certificate and Installation Packages for Microsoft Windows and Linux Computers

|  |  |
| --- | --- |
| This command generates Veeam Installer Service Veeam Deployer Service certificates and installation packages for Microsoft Windows and Linux computers to the C:\Users\Administrator\Documents folder.  |  | | --- | | Generate-VBRBackupServerDeployerKit -ExportPath "C:\Users\Administrator\Documents" -AllPlatforms | |


