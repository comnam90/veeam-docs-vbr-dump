---
title: "Add-StoragePluginHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-storagepluginhost.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-StoragePluginHost

In this article

Short Description

Adds Universal Storage API integrated systems to Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

This cmdlet provides parameter sets that allow you to:

* Add storage systems by a username and password.

|  |
| --- |
| Add-StoragePluginHost -PluginType <string> -Name <string> -UserName <string> -Password <string> [-Description <string>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-MountServer <CHost>] [-Port <int>] [-SkipRescan] [-Force] [-iSCSI] [-FibreChannel] [-NVMe] [-Nfs] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRNASProxyServer[]>] [-EnableVMwareBackup] [-EnableAgentBackup]  [<CommonParameters>] |

* Add storage systems by credentials.

|  |
| --- |
| Add-StoragePluginHost -PluginType <string> -Name <string> -Credentials <CInternalCredentials> [-Description <string>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>][-MountServer <CHost>] [-Port <int>] [-SkipRescan] [-Force] [-iSCSI] [-FibreChannel] [-NVMe] [-Nfs] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRNASProxyServer[]>] [-EnableVMwareBackup] [-EnableAgentBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet adds selected Universal Storage API integrated systems to backup infrastructure.

When you add storage systems to your backup infrastructure, Veeam Backup & Replication performs a rescan of storage systems. During the rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

For more information about the rescan, see the [Adding Storage Systems](https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_add_storage.html?ver=13) section of the User Guide.

|  |
| --- |
| ![Add-StoragePluginHost](images/icon_tip.webp) Tip: |
| Use the SkipRescan parameter to skip the automatic rescan.  To rescan storage systems manually, use the following cmdlets:   * Run [Sync-StoragePluginHost](sync-storagepluginhost.md) to rescan of the entire storage system. * Run [Sync-StoragePluginVolume](sync-storagepluginvolume.md) to rescan selected integrated systems volumes added to backup infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| PluginType | Specifies the storage plug-in.  The cmdlet will use this plug-in for adding the associated storage to Veeam Backup & Replication. | String | True | Named | False |
| Name | Specifies the storage IP address or DNS name of the storage you want to add. | String | True | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| MountServer | Specifies the mount server that you want to use to work with this storage. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| WindowsMountServer | Specifies Windows mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| LinuxMountServer | Specifies Linux mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Port | Sets a port used to connect to the storage. By default, port 443 is used. | Int. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a ThinkSystem storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableVMwareBackup | Enables the VMware backup option.  If you provide this parameter, you will be able to use storage snapshots to backup and restore VMware vSphere VMs hosted on storage systems. | SwitchParameter | False | Named | False |
| EnableAgentBackup | Enables the Veeam Agent backup option.  Defines that the cmdlet will allow backup of Veeam Agents.  If you provide this parameter, you will be able to integrate your storage systems with Veeam Agent for Microsoft Windows installed on computers in your infrastructure. | SwitchParameter | False | Named | False |
| Proxy | For the EnableVMwareBackup parameter.  Specifies an array of proxies you want to use with this storage.  If not set, Veeam Backup & Replication will use automatic proxy selection. | Accepts the IProxy[] object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| iSCSI | For the EnableVMwareBackup parameter.  Defines that the storage works over the iSCSI protocol. | SwitchParameter | False | Named | False |
| NFS | For the EnableVMwareBackup parameter.  Defines that the storage works over the NFS protocol. | SwitchParameter | False | Named | False |
| FibreChannel | For the EnableVMwareBackup parameter.    Defines that the storage works over the FibreChannel protocol. | SwitchParameter | False | Named | False |
| NVMe | For the EnableVMwareBackup parameter. Defines that the storage works over the NVMe protocol. | SwitchParameter | False | Named | False |
| AgentFC | For the EnableAgentBackup parameter.  Defines that the storage works over the FS protocol. | SwitchParameter | False | Named | False |
| AgentISCSI | For the EnableAgentBackup parameter.  Defines that the storage works over the iSCSI protocol. | SwitchParameter | False | Named | False |
| AgentProxy | For the EnableAgentBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRComputerFileProxyServer object. To create this object, run the [Add-VBRComputerFileProxyServer](add-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Adding IBM Spectrum Virtualize Storage System

This example shows how to add an IBM Spectrum Virtualize storage system to Veeam Backup & Replication.

|  |
| --- |
| Get-VBRStoragePlugin  $credentials = Get-VBRCredentials -Name "IBM Administrator"  $proxy = Get-VBRViProxy -Name 172.17.41.34  Add-StoragePluginHost -PluginType Ibm -Name 172.17.41.3 -Credentials $credentials -Description "IBM iSCSI" -Proxy $proxy |

Perform the following steps:

1. Run the [Get-VBRStoragePlugin](get-vbrstorageplugin.md) cmdlet. To add the IBM Spectrum Virtualize storage system to Veeam Backup & Replication, you will need the IBM Plug-in.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable.
3. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
4. Run the Add-StoragePluginHost cmdlet. Specify the following settings:

* Set the Ibm option for the PluginType parameter value.
* Specify the Name parameter value.
* Set the $credentials variable as the Credentials parameter value.
* Specify the Description parameter value.
* Set the $proxy variable as the Proxy parameter value.

Related Commands

* [Get-VBRStoragePlugin](get-vbrstorageplugin.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
