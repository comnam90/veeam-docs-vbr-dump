---
title: "Set-VNXHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vnxhost.html"
last_updated: "7/16/2025"
product_version: "13.0.1.1071"
---

# Set-VNXHost

In this article

Short Description

Modifies Dell VNX storage settings.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Set-VNXHost -Host <CVnxHost> [-Description <string>] [-UserName <string>] [-Password <string>] [-Credentials <CInternalCredentials>] [-CredentialsScope {Global | Local | LDAP}] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-MountServer <CHost>] [-IncludedVolume <CSanInfrastructureVolume[]>] [-ExcludedVolume <CSanInfrastructureVolume[]>] [-IncludedWildcard <string[]>] [-ExcludedWildcard <string[]>] [-AgentProxy <VBRNASProxyServer[]>] [-AgentVolumeScanType {All | Exclude | Include}] [-AgentIncludedVolume <CSanInfrastructureVolume[]>] [-AgentExcludedVolume <CSanInfrastructureVolume[]>] [-AgentIncludedWildcard <string[]>] [-AgentExcludedWildcard <string[]>] [-SkipRescan] [-Force] [-EnableProxyAutoSelection] [-ProtocolPolicy <VBRStorageProtocolPolicy>] [-VolumeScanType {All | Exclude | Include}] [-AgentEnableProxyAutoSelection] [-AgentProtocolPolicy <VBRStorageProtocolPolicy>] [-EnableVMwareBackup] [-EnableAgentBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Dell VNX storage systems. When you modify storage system settings, the cmdlet automatically rescans storage systems.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Tip |
| You can specify the scope of volumes that you want to rescan with the VBRVolumeScanType parameter.  Run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet to get an array of volumes from Dell VNX storage systems. |

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to modify. | Accepts the CVnxHost object. To create this object, run the [Get-VNXHost](get-vnxhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Description | Specifies the description of the storage. | String | False | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| CredentialsScope | Used to authenticate with the VNXBlock.  Specifies the credentials scope: Global, Local, LDAP. | VBRVNXBlockCredentialsScope | False | Named | False |
| MountServer | Specifies the mount server that you want to use to work with this storage. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet | False | Named | False |
| WindowsMountServer | Specifies Windows mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| LinuxMountServer | Specifies Linux mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| EnableAgentBackup | Enables the Veeam Agent backup option.  If you provide this parameter, you will be able to integrate your storage systems with Veeam Agent for Microsoft Windows installed on computers in your infrastructure. | SwitchParameter | False | Named | False |
| Proxy | For the EnableVMwareBackup parameter.  Specifies the array of proxies you want to use. | String | False | Named | False |
| EnableProxyAutoSelection | For the EnableVMwareBackup parameter.  Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| ProtocolPolicy | For the EnableVMwareBackup parameter.  Specifies the protocol policy for the storage. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |
| VolumeScanType | For the EnableVMwareBackup parameter.  Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes. Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| IncludedVolume | For the VolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet. | False | Named | False |
| IncludedWildcard | For the VolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| ExcludedVolume | For the VolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet. | False | Named | False |
| ExcludedWildcard | For the VolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentProxy | For the EnableAgentBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRComputerFileProxyServer object. To create this object, run the [Add-VBRComputerFileProxyServer](add-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |
| AgentVolumeScanType | For the EnableAgentBackup parameter.  Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes.  Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| AgentIncludedVolume | For the AgentVolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet. | False | Named | False |
| AgentExcludedVolume | For the AgentVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet. | False | Named | False |
| AgentIncludedWildcard | For the AgentVolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentExcludedWildcard | For the AgentVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentEnableProxyAutoSelection | For the EnableAgentBackup parameter.  Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| AgentProtocolPolicy | For the EnableAgentBackup parameter.  Specifies the protocol policy for the storage. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a Dell VNX storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Automatic Proxy Selection for Dell VNX Storage System

|  |  |
| --- | --- |
| This example shows how to enable the automatic proxy selection for a Dell VNX storage system.  |  | | --- | | $storage = Get-VNXHost -Name "VNX Storage"  Set-VNXHost -Host $storage -EnableProxyAutoSelection |  Perform the following steps:   1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Set-VNXHost cmdlet. Set the $storage variable as the Host parameter value. Provide the EnableProxyAutoSelection parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Excluding Dell VNX Volumes from Rescan

|  |  |
| --- | --- |
| This example shows how to exclude Dell VNX volumes from rescan.  |  | | --- | | $storage = Get-VNXHost -Name "VNX Storage"  $volumes = Get-VNXInfrastructureVolume -Name "ISCSI Volume4", "ISCSI Volume5", "NFS Volume1"  Set-VNXHost -Host $storage -VolumeScanType Exclude -ExcludedVolume $volumes |  Perform the following steps:   1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volumes variable. 3. Run the Set-VNXHost cmdlet. Set the $storage variable as the Host parameter value. Set the Exclude option for the VolumeScanType parameter. Set the $volumes variable as the ExcludedVolume parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Rescanning All Volumes Added to Dell VNX Storage System

|  |  |
| --- | --- |
| This example shows how to rescan all volumes added to a Dell VNX storage system.  |  | | --- | | $storage = Get-VNXHost -Name "VNX Storage"  $volumes = Get-VNXInfrastructureVolume -Host $storage  Set-VNXHost -Host $storage -VolumeScanType Include -Included $volumes |  Perform the following steps:   1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet. Set the $storage variable as the Host parameter value. Save the result to the $volumes variable. 3. Run the Set-VNXHost cmdlet. Set the $storage variable as the Host parameter value. Set the Include option for the VolumeScanType parameter. Set the $volumes variable as the Included parameter value. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md)

Page updated 7/16/2025

Page content applies to build 13.0.1.1071
