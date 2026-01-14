---
title: "Set-StoragePluginHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-storagepluginhost.html"
last_updated: "7/16/2025"
product_version: "13.0.1.1071"
---

# Set-StoragePluginHost

In this article

Short Description

Modifies settings of Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Set-StoragePluginHost -Host <CPublicPluginHost> [-Description <string>] [-UserName <string>] [-Password <string>] [-Credentials <CInternalCredentials>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-MountServer <CHost>] [-Port <int>] [-VolumeScanType {All | Exclude | Include}] [-IncludedVolume <CSanInfrastructureVolume[]>] [-ExcludedVolume <CSanInfrastructureVolume[]>] [-IncludedWildcard <string[]>] [-ExcludedWildcard <string[]>] [-AgentProxy <VBRNASProxyServer[]>] [-AgentVolumeScanType {All | Exclude | Include}] [-AgentIncludedVolume <CSanInfrastructureVolume[]>] [-AgentExcludedVolume <CSanInfrastructureVolume[]>] [-AgentIncludedWildcard <string[]>] [-AgentExcludedWildcard <string[]>] [-SkipRescan] [-Force] [-EnableProxyAutoSelection] [-ProtocolPolicy <VBRStorageProtocolPolicy>] [-AgentEnableProxyAutoSelection] [-AgentProtocolPolicy <VBRStorageProtocolPolicy>] [-EnableVMwareBackup] [-EnableAgentBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Universal Storage API storage systems. When you modify storage system settings, the cmdlet automatically rescans storage systems.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Tip |
| You can specify the scope of volumes that you want to rescan with the VBRVolumeScanType parameter.  Run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet to get an array of volumes from Universal Storage API integrated systems. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to modify. | Accepts the CPublicPluginHost object. To get this object, run the[Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Description | Specifies the description of the storage. | String | False | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| MountServer | Specifies the mount server that you want to use to work with this storage. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| WindowsMountServer | Specifies Windows mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| LinuxMountServer | Specifies Linux mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| EnableVMwareBackup | Enables the VMware backup option.  If you provide this parameter, you will be able to use storage snapshots to backup and restore VMware vSphere VMs hosted on storage systems. | SwitchParameter | False | Named | False |
| EnableAgentBackup | Enables the Veeam Agent backup option.  If you provide this parameter, you will be able to integrate your storage systems with Veeam Agent for Microsoft Windows installed on computers in your infrastructure. | SwitchParameter | False | Named | False |
| Proxy | For the EnableVMwareBackup parameter.  Specifies the array of proxies you want to use to work with this storage.  Note: All previously used proxies will be unassigned from the storage.  If you want Veeam to choose a proxy for your storage automatically, use the EnableProxyAutoSelection parameter. | Accepts the IProxy[] object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| EnableProxyAutoSelection | For the EnableVMwareBackup parameter.  Defines that Veeam Backup & Replication will select a proxy automatically.  If you want to select proxies for the storage yourself, use the Proxy parameter. | SwitchParameter | False | Named | False |
| ProtocolPolicy | For the EnableVMwareBackup parameter.  Specifies the protocol policy for the storage. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |
| VolumeScanType | For the EnableVMwareBackup parameter.  Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes. Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| IncludedVolume | For the VolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet. | False | Named | False |
| IncludedWildcard | For the VolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| ExcludedVolume | For the VolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet. | False | Named | False |
| ExcludedWildcard | For the VolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentProxy | For the EnableAgentBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRComputerFileProxyServer object. To create this object, run the [Add-VBRComputerFileProxyServer](add-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |
| AgentVolumeScanType | For the EnableAgentBackup parameter.  Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes. Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| AgentIncludedVolume | For the AgentVolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet. | False | Named | False |
| AgentExcludedVolume | For the AgentVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet. | False | Named | False |
| AgentIncludedWildcard | For the AgentVolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentExcludedWildcard | For the AgentVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentEnableProxyAutoSelection | For the EnableAgentBackup parameter.  Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| AgentProtocolPolicy | For the EnableAgentBackup parameter.  Specifies the protocol policy for the storage. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assigning New Backup Proxy to Storage System

|  |  |
| --- | --- |
| This example shows how to assign a new backup proxy to a storage system.  |  | | --- | | $storage = Get-StoragePluginHost -Name "IBM Spectrum"  $proxy = Get-VBRViProxy -Name "LocalProxy"  Set-StoragePluginHost -Host $storage -Proxy $proxy |  Perform the following steps:   1. Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 3. Run the Set-StoragePluginHost cmdlet. Set the $storage variable as the Host parameter value. Set the $proxy variable as the Proxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Excluding Volumes from Rescan

|  |  |
| --- | --- |
| This example shows how to exclude volumes from of a Universal Storage API integrated system from rescan.  |  | | --- | | $storage = Get-VNXHost -Name "VNX Storage"  $volumes = Get-StoragePluginInfrastructureVolume -Name "ISCSI Volume4", "ISCSI Volume5", "NFS Volume1"  Set-StoragePluginHost -Host $storage -VolumeScanType Exclude -ExcludedVolume $volumes |  Perform the following steps:   1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volumes variable. 3. Run the Set-StoragePluginHost cmdlet. Set the $storage variable as the Host parameter value. Set the Exclude option for the VolumeScanType parameter. Set the $volumes variable as the ExcludedVolume parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Rescanning All Volumes Added to Univeral Storage API Integrated System

|  |  |
| --- | --- |
| This example shows how to rescan all volumes added to a Universal Storage API integrated system.  |  | | --- | | $storage = Get-VNXHost -Name "VNX Storage"  $volumes = Get-StoragePluginInfrastructureVolume -Host $storage  Set-StoragePluginHost -Host $storage -VolumeScanType Include -Included $volumes |  Perform the following steps:   1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet. Set the $storage variable as the Host parameter value. Save the result to the $volumes variable. 3. Run the Set-StoragePluginHost cmdlet. Set the $storage variable as the Host parameter value. Set the Include option for the VolumeScanType parameter. Set the $volumes variable as the Included parameter value. |

Related Commands

* [Get-StoragePluginHost](get-storagepluginhost.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md)
* [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md)

Page updated 7/16/2025

Page content applies to build 13.0.1.1071
