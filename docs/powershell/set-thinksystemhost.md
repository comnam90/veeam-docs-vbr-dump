---
title: "Set-ThinkSystemHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-thinksystemhost.html"
last_updated: "7/16/2025"
product_version: "13.0.1.1071"
---

# Set-ThinkSystemHost


Short Description

Modifies ThinkSystem storage system settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-ThinkSystemHost -Host <CNaHost> [-Name <string>] [-Description <string>] [-UserName <string>] [-Password <string>] [-Credentials <CInternalCredentials>] [-IsHTTP <bool>] [-Port <int>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>][-MountServer <CHost>] [-VolumeScanType {All | Exclude | Include}] [-IncludedVolume <CSanInfrastructureVolume[]>] [-ExcludedVolume <CSanInfrastructureVolume[]>] [-IncludedWildcard <string[]>] [-ExcludedWildcard <string[]>] [-NASProxy <VBRNASProxyServer[]>] [-NASVolumeScanType {All | Exclude | Include}] [-NASIncludedVolume <CSanInfrastructureVolume[]>] [-NASExcludedVolume <CSanInfrastructureVolume[]>] [-NASIncludedWildcard <string[]>] [-NASExcludedWildcard <string[]>] [-AgentProxy <VBRNASProxyServer[]>] [-AgentVolumeScanType {All | Exclude | Include}] [-AgentIncludedVolume <CSanInfrastructureVolume[]>] [-AgentExcludedVolume <CSanInfrastructureVolume[]>] [-AgentIncludedWildcard <string[]>] [-AgentExcludedWildcard <string[]>] [-SkipRescan] [-Force] [-EnableProxyAutoSelection] [-ProtocolPolicy <VBRStorageProtocolPolicy>] [-NASEnableProxyAutoSelection] [-NASProtocolPolicy <VBRStorageProtocolPolicy>] [-AgentEnableProxyAutoSelection] [-AgentProtocolPolicy <VBRStorageProtocolPolicy>] [-EnableVMwareBackup] [-EnableNASBackup] [-EnableAgentBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of ThinkSystem storage systems. When you modify storage system settings, the cmdlet automatically rescans storage systems.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Tip |
| You can specify the scope of volumes that you want to rescan with the VBRVolumeScanType parameter.  Run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet to get an array of volumes from ThinkSystem storage system. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage that you want to modify. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the storage IP address or DNS name. | String | True | Named | False |
| Description | Specifies a description of the storage. | String | False | Named | False |
| UserName | Specifies a user name that you want to use for authenticating with the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| Credentials | Specifies the credentials record you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| IsHTTP | Defines whether the cmdlet uses the HTTP protocol to connect to the ThinkSystem.  True: The cmdlet will connect to the ThinkSystem through HTTP protocol.  False: The cmdlet will connect to the ThinkSystem through HTTPS protocol.  Default: True | Bool | False | Named | False |
| Port | Specifies the port for connecting with the ThinkSystem storage.  Default: 443. | Int | False | Named | False |
| MountServer | Specifies the mount server that you want to use to work with this storage. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| WindowsMountServer | Specifies Windows mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| LinuxMountServer | Specifies Linux mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| EnableVMwareBackup | Enables the VMware backup option.  If you provide this parameter, you will be able to use storage snapshots to backup and restore VMware vSphere VMs hosted on storage systems. | SwitchParameter | False | Named | False |
| EnableNASBackup | Enables the file backup option.  If you provide this parameter, you will be able to integrate your storage systems with NAS file shares added to your infrastructure. | SwitchParameter | False | Named | False |
| EnableAgentBackup | Enables the Veeam Agent backup option.  If you provide this parameter, you will be able to integrate your storage systems with Veeam Agent for Microsoft Windows installed on computers in your infrastructure. | SwitchParameter | False | Named | False |
| Proxy | For the EnableVMwareBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the IProxy[] object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| VolumeScanType | For the EnableVMwareBackup parameter.  Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes. Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| IncludedVolume | For the VolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. | False | Named | False |
| IncludedWildcard | For the VolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| ExcludedVolume | For the VolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. | False | Named | False |
| ExcludedWildcard | For the VolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| NASProxy | For the EnableNASBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRNASProxyServer object. To create this object, run the [Add-VBRNASProxyServer](add-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| NASVolumeScanType | For the EnableNASBackup parameter.  Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes.  Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| NASIncludedVolume | For the NASVolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. | False | Named | False |
| NASExcludedVolume | For the NASVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. | False | Named | False |
| NASIncludedWildcard | For the NASVolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| NASExcludedWildcard | For the NASVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentProxy | For the EnableAgentBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRComputerFileProxyServer object. To create this object, run the [Add-VBRComputerFileProxyServer](add-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |
| AgentVolumeScanType | For the EnableAgentBackup parameter.  Specifies the scope of volumes that you want to rescan.  You can use the following options to rescan the volumes:   * All - choose this option to scan all volumes that were added to your backup infrastructure with the initial scan. * Exclude - choose this option to exclude volumes from scan. Note: Veeam Backup & Replication will not show excluded volumes in the backup infrastructure after the rescan. Use the ExcludedVolume parameter to specify the excluded volumes. * Include - choose this option to scan only the specified storage volumes. Use the IncludedVolume parameter to specify the included volumes. | VBRVolumeScanType | False | Named | False |
| AgentIncludedVolume | For the AgentVolumeScanType parameter with the include option.  Specifies an array of storage volumes that you want to rescan.  Note: Veeam Backup & Replication will show only rescanned volumes in the backup infrastructure. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. | False | Named | False |
| AgentExcludedVolume | For the AgentVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes that you do not want to rescan.  Note: Veeam Backup & Replication will not show the excluded volumes in the backup infrastructure after the rescan. | Accepts the CSanInfrastructureVolume[] object. To create this object, run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. | False | Named | False |
| AgentIncludedWildcard | For the AgentVolumeScanType parameter with the include option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will rescan only those volumes which names are specified with these wildcard characters. | String | False | Named | False |
| AgentExcludedWildcard | For the AgentVolumeScanType parameter with the exclude option.  Specifies an array of storage volumes with wildcard characters. Veeam Backup & Replication will not rescan the volumes which names are specified with these wildcard characters. | String | False | Named | False |
| EnableProxyAutoSelection | For the EnableVMwareBackup parameter.  Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| ProtocolPolicy | For the EnableVMwareBackup parameter.  Specifies the protocol policy for the storage. | SwitchParameter | False | False | False |
| NASEnableProxyAutoSelection | For the EnableNASBackup parameter.  Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| NASProtocolPolicy | For the EnableNASBackup parameter.  Specifies the protocol policy for the storage. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |
| AgentEnableProxyAutoSelection | For the EnableAgentBackup parameter.  Defines that Veeam Backup & Replication will use automatic proxy selection. | SwitchParameter | False | Named | False |
| AgentProtocolPolicy | For the EnableAgentBackup parameter.  Specifies the protocol policy for the storage. | Accepts the VBRStorageProtocolPolicy object. To create this object, run the [New-VBRStorageProtocolPolicy](new-vbrstorageprotocolpolicy.md) cmdlet. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a ThinkSystem storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Changing NetApp Port Number and Protocol

|  |  |
| --- | --- |
| This example shows how to change the port number and protocol for connecting with NetApp storage system.  |  | | --- | | $storage = Get-ThinkSystemHost -Name "ThinkSystem Store"  Set-ThinkSystemHost -Host $storage -IsHTTP:$true -Port 80 |  Perform the following steps:   1. Run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Set-ThinkSystemHost cmdlet. Specify the following settings:  * Set the $storage variable as the Host parameter value. * Provide the IsHTTP parameter value. * Provide the Port parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Excluding Storage Volumes from Rescan Session

|  |  |
| --- | --- |
| This example shows how to exclude specified ThinkSystem storage volumes from the rescan session.  |  | | --- | | $storage = Get-ThinkSystemHost -Name "ThinkSystem Store"  $volumes = Get-ThinkSystemInfrastructureVolume -Name "ISCSI Volume4", "ISCSI Volume5", "NFS Volume1"  Set-ThinkSystemHost -Host $storage -VolumeScanType Exclude -ExcludedVolume $volumes |  Perform the following steps:   1. Run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volumes variable. 3. Run the Set-ThinkSystemHost cmdlet. Specify the following settings:  * Set the $storage variable as the Host parameter value. * Set the Exclude option for the VolumeScanType parameter. * Set the $volumes variable as the ExcludedVolume parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Rescanning All Storage Volumes

|  |  |
| --- | --- |
| This example shows shows how to rescan all volumes added to a ThinkSystem storage system.  |  | | --- | | $storage = Get-ThinkSystemHost -Name "ThinkSystem Store"  $volumes = Get-ThinkSystemInfrastructureVolume -Host $storage  Set-ThinkSystemHost -Host $storage -VolumeScanType Include -Included $volumes |  Perform the following steps:   1. Run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md) cmdlet. Specify the Host parameter value. Save the result to the $volumes variable. 3. Run the Set-ThinkSystemHost cmdlet. Specify the following settings:  * Set the $storage variable as the Host parameter value.  * Set the Include option for the VolumeScanType parameter.  * Set the $volumes variable as the Included parameter value. |

Related Commands

* [Get-ThinkSystemHost](get-thinksystemhost.md)
* [Get-ThinkSystemInfrastructureVolume](get-thinksysteminfrastructurevolume.md)


