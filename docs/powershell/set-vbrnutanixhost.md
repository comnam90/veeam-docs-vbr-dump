---
title: "Set-VBRNutanixHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnutanixhost.html"
last_updated: "2/7/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNutanixHost

In this article

Short Description

Modifies Nutanix Files storage system settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNutanixHost -Host <CNutanixHost> [-Name <string>] [-Description <string>] [-UserName <string>] [-Password <string>] [-Credentials <CInternalCredentials>] [-Port <int>] [-NASProxy <VBRNASProxyServer[]>] [-NASVolumeScanType {All | Exclude | Include}] [-NASIncludedVolume <CSanInfrastructureVolume[]>] [-NASExcludedVolume <CSanInfrastructureVolume[]>] [-NASIncludedWildcard <string[]>] [-NASExcludedWildcard <string[]>] [-SkipRescan] [-Force] [-NASEnableProxyAutoSelection] [-NASProtocolPolicy <VBRStorageProtocolPolicy>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Nutanix Files storage systems. When you modify storage system settings, the cmdlet automatically rescans storage systems.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage system you want to modify. | Accepts the CNutanixHost object. To create this object, run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name of the storage system that you want to modufy. | String | False | Named | False |
| Description | Specifies the description of the storage system. | String | False | Named | False |
| UserName | Specifies the user name that you want to use for authentication to the storage system. | String | False | Named | False |
| Password | Specifies the password you want to use for authentication to the storage system. | String | False | Named | False |
| Credentials | Specifies the credentials that you want to use for authentication to the storage system. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Port | Specifies the port used to connect to the storage system. | Int | False | Named | False |
| NASProxy | Specifies the array of proxies you want to use. | Accepts the VBRNASProxyServer object. To create this object, run the [Add-VBRNASProxyServer](add-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| NASVolumeScanType | Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All: choose this option to rescan all volumes that were added to your backup infrastructure with the initial rescan. * Exclude: choose this option to exclude volumes from rescan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include: choose this option to rescan only the specified storage volumes. Use the IncludedVolume parameter to specify the included volumes. | Accepts the VBRVolumeScanType enum type. | False | Named | False |
| NASIncludedVolume | For the NASVolumeScanType parameter set to Include.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-VBRNutanixInfrastructureVolume](get-vbrnutanixinfrastructurevolume.md) cmdlet. | False | Named | False |
| NASExcludedVolume | For the NASVolumeScanType parameter set to Exclude.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-VBRNutanixInfrastructureVolume](get-vbrnutanixinfrastructurevolume.md) cmdlet. | False | Named | False |
| NASIncludedWildcard | For the NASVolumeScanType parameter set to Include.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | string[] | False | Named | False |
| NASExcludedWildcard | For the NASVolumeScanType parameter set to Exclude.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | string[] | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start rescan automatically setting of the storage system are modified. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify the storage system settings without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| NASEnableProxyAutoSelection | Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| NASProtocolPolicy | Specifies the protocol policy for the storage system. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CNutanixHost object that defines the settings of a Nutanix Files storage system.

Examples

Modifying Port Number of Nutanix Files Storage Systems

This example shows how to modify the port number of Nutanix Files Storage Systems.

|  |
| --- |
| $host = Get-VBRNutanixHost -Name "Nutanix Files\_host"  Set-VBRNutanixHost -Host $host -Port 80 |

Perform the following steps:

1. Run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet to create a credential object. Specify the Name parameter value. Save the result to the $host variable.
2. Run the Set-VBRNutanixHost cmdlet. Set the $host variable as the Host parameter value.Specify the Port parameter value.

Related Commands

[Get-VBRNutanixHost](get-vbrnutanixhost.md)

Page updated 2/7/2024

Page content applies to build 13.0.1.1071
