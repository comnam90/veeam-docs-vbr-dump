---
title: "Set-VBRIsilonHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrisilonhost.html"
last_updated: "3/27/2024"
product_version: "13.0.1.1071"
---

# Set-VBRIsilonHost

In this article

Short Description

Modifies Dell PowerScale (formerly Isilon) storage settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRIsilonHost -Host <CIsilonHost> [-Name <string>] [-Description <string>] [-UserName <string>] [-Password <string>] [-Credentials <CInternalCredentials>] [-Port <int>] [-NASProxy <VBRNASProxyServer[]>] [-NASVolumeScanType {All | Exclude | Include}] [-NASIncludedVolume <CSanInfrastructureVolume[]>] [-NASExcludedVolume <CSanInfrastructureVolume[]>] [-NASIncludedWildcard <string[]>] [-NASExcludedWildcard <string[]>] [-SkipRescan] [-Force] [-NASEnableProxyAutoSelection] [-NASProtocolPolicy <VBRStorageProtocolPolicy>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Dell PowerScale storage systems. When you modify storage system settings, the cmdlet automatically rescans storage systems.

To modify settings, enter the necessary parameters with new values. The parameters that you omit will remain unchanged.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Tip |
| You can specify the scope of volumes that you want to rescan with the VBRVolumeScanType parameter.  Run the [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md) cmdlet to get an array of volumes from Dell PowerScale storage systems. |

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to modify. | Accepts the CIsilonHost object. To get this object, run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name of the storage. | String | False | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add a Dell PowerScale without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| Port | Sets a port used to connect to the PowerScale storage. | Int | False | Named | False |
| NASProxy | Specifies the array of proxies you want to use. | Accepts the VBRNASProxyServer object. To create this object, run the [Add-VBRNASProxyServer](add-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| NASEnableProxyAutoSelection | Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| NASProtocolPolicy | Specifies the protocol policy for the storage. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |
| NASVolumeScanType | Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes. Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| NASIncludedVolume | For the NASVolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To get this object, run the [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md) cmdlet. | False | Named | False |
| NASIncludedWildcard | For the NASVolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| NASExcludedVolume | For the NASVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To get this object, run the [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md) cmdlet. | False | Named | False |
| NASExcludedWildcard | For the NASVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Excluding Dell PowerScale Volumes from Rescan

|  |  |
| --- | --- |
| This example shows how to exclude the Isilon Storage Dell PowerScale volumes from rescan.  |  | | --- | | $storage = Get-VBRIsilonHost -Name "Isilon Storage"  $volumes = Get-VBRIsilonInfrastructureVolume -Name "Volume4", "Volume5"  Set-VBRIsilonHost -Host $storage -NASVolumeScanType Exclude -NASExcludedVolume $volumes |  Perform the following steps:   1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Provide the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md) cmdlet. Provide the Name parameter value. Save the result to the $volumes variable. 3. Run the Set-VBRIsilonHost cmdlet. Specify the following settings:  * Set the $storage variable as the Host parameter value. * Set the Exclude option for the NASVolumeScanType parameter. * Set the $volumes variable as the NASExcludedVolume parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Rescanning All Dell PowerScale Volumes

|  |  |
| --- | --- |
| This example shows how to rescan all volumes added to the Isilon Storage Dell PowerScale storage system.  |  | | --- | | $storage = Get-VBRIsilonHost -Name "Isilon Storage"  $volumes = Get-VBRIsilonInfrastructureVolume -Host $storage  Set-VBRIsilonHost -Host $storage -VolumeScanType Include -Included $volumes |  Perform the following steps:   1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Provide the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md) cmdlet. Provide the Host parameter value. Save the result to the $volumes variable. 3. Run the Set-VBRIsilonHost cmdlet. Specify the following settings:  * Set the $storage variable as the Host parameter value. * Set the Include option for the VolumeScanType parameter value. * Set the $volumes variable as the Included parameter value. |

Related Commands

* [Get-VBRIsilonHost](get-vbrisilonhost.md)
* [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md)

Page updated 3/27/2024

Page content applies to build 13.0.1.1071
