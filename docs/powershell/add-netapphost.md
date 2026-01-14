---
title: "Add-NetAppHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-netapphost.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-NetAppHost

In this article

Short Description

Adds NetApp storage systems to Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add storage systems by a user name and a password.

|  |
| --- |
| Add-NetAppHost -Name <string> -UserName <string> -Password <string> [-Description <string>] [-IsHTTP <bool>] [-Port <int>] [-Proxy <IProxy[]>] [-MountServer <CHost>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-NASProxy <VBRNASProxyServer[]>] [-SkipRescan] [-Force] [-iSCSI] [-NFS] [-FibreChannel] [-NVMe] [-CreateRulesAutomatically] [-NASNFS] [-NASSMB] [-NASCreateRulesAutomatically] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRNASProxyServer[]>] [-EnableVMwareBackup] [-EnableNASBackup] [-EnableAgentBackup]  [<CommonParameters>] |

* Add storage systems by credentials.

|  |
| --- |
| Add-NetAppHost -Name <string> -Credentials <CInternalCredentials> [-Description <string>] [-IsHTTP <bool>] [-Port <int>] [-Proxy <IProxy[]>] [-MountServer <CHost>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>][-NASProxy <VBRNASProxyServer[]>] [-SkipRescan] [-Force] [-iSCSI] [-NFS] [-FibreChannel] [-NVMe] [-CreateRulesAutomatically] [-NASNFS] [-NASSMB] [-NASCreateRulesAutomatically] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRNASProxyServer[]>] [-EnableVMwareBackup] [-EnableNASBackup] [-EnableAgentBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet adds selected NetApp storage systems to backup infrastructure.

When you add storage systems to your backup infrastructure, Veeam Backup & Replication performs a rescan of storage systems. During the rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

For more information about the rescan, see the [Adding Storage Systems](https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_add_storage.html?ver=13) section of the User Guide.

|  |
| --- |
| ![Add-NetAppHost](images/icon_tip.webp) Tip: |
| Use the SkipRescan parameter to skip the automatic rescan.  To rescan storage systems manually, use the following cmdlets:   * Run [Sync-NetAppHost](sync-netapphost.md) to rescan of the entire storage system. * Run [Sync-NetAppVolume](sync-netappvolume.md) to rescan selected NetApp volumes added to backup infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the storage IP address or DNS name. | String | True | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| IsHTTP | If set to TRUE, HTTP protocol will be used to connect to the NetApp storage. Otherwise, HTTPS protocol will be selected. By default, HTTPS is used. | Bool | False | Named | False |
| Port | Sets a port used to connect to the NetApp storage. By default, port 443 is used. | Int. | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| MountServer | Specifies the mount server that you want to use to work with this storage. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| WindowsMountServer | Specifies Windows mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| LinuxMountServer | Specifies Linux mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a ThinkSystem storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableVMwareBackup | Enables the VMware backup option.  If you provide this parameter, you will be able to use storage snapshots to backup and restore VMware vSphere VMs hosted on storage systems. | SwitchParameter | False | Named | False |
| EnableNASBackup | Enables the file backup option.  If you provide this parameter, you will be able to integrate your storage systems with NAS file shares added to your infrastructure. | SwitchParameter | False | Named | False |
| EnableAgentBackup | Enables the Veeam Agent backup option.  If you provide this parameter, you will be able to integrate your storage systems with Veeam Agent for Microsoft Windows installed on computers in your infrastructure. | SwitchParameter | False | Named | False |
| Proxy | For the EnableVMwareBackup parameter.  Specifies an array of proxies you want to use with this storage.  If not set, Veeam Backup & Replication will use automatic proxy selection. | Accepts the IProxy[] object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| iSCSI | For the EnableVMwareBackup parameter.  Defines that the storage works over the iSCSI protocol. | SwitchParameter | False | Named | False |
| NFS | For the EnableVMwareBackup parameter.  Defines that the storage works over the NFS protocol. | SwitchParameter | False | Named | False |
| FibreChannel | For the EnableVMwareBackup parameter.  Defines that the storage works over the FibreChannel protocol. | SwitchParameter | False | Named | False |
| NVMe | For the EnableVMwareBackup parameter. Defines that the storage works over the NVMe protocol. | SwitchParameter | False | Named | False |
| CreateRulesAutomatically | For the EnableVMwareBackup parameter.  Defines that the cmdlet will allow Veeam Backup & Replication to automatically create required SMB and NFS export rules on the storage system.  If you provide this parameter, the rules will be created automatically in case the proxies are unavailable. | SwitchParameter | False | Named | False |
| NASNFS | For the EnableNASBackup parameter.  Defines that the storage works over the NFS protocol. | SwitchParameter | False | Named | False |
| NASSMB | For the EnableNASBackup parameter.  Defines that the storage works over the SMB protocol. | SwitchParameter | False | Named | False |
| NASProxy | For the EnableNASBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRNASProxyServer object. To create this object, run the [Add-VBRNASProxyServer](add-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| NASCreateRulesAutomatically | For the EnableNASBackup parameter.  Defines that the cmdlet will allow Veeam Backup & Replication to automatically create required SMB and NFS export rules on the storage system.  If you provide this parameter, the rules will be created automatically in case the proxies are unavailable. | SwitchParameter | False | Named | False |
| AgentFC | For the EnableAgentBackup parameter.  Defines that the storage works over the FS protocol. | SwitchParameter | False | Named | False |
| AgentISCSI | For the EnableAgentBackup parameter.  Defines that the storage works over the iSCSI protocol. | SwitchParameter | False | Named | False |
| AgentProxy | For the EnableAgentBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRComputerFileProxyServer object. To create this object, run the [Add-VBRComputerFileProxyServer](add-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Adding NetApp Storage System

This example shows how to add a NetApp storage system to backup infrastructure using credentials.

|  |
| --- |
| $credentials = Get-VBRCredentials -Name "NetApp Administrator"  $proxy = Get-VBRViProxy -Name 167.16.21.25  Add-NetAppHost -Name 167.16.2.134 -Credentials $credentials -Proxy $proxy -Description "NetApp Storage" |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable.
2. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
3. Run the Add-VBRNetAppHost cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $credentials variable as the Credentials parameter value.
* Set the $proxy variable as the Proxy parameter value.
* Specify the Description parameter value.

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRViProxy](get-vbrviproxy.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
