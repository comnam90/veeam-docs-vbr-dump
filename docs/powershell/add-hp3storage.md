---
title: "Add-HP3Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-hp3storage.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-HP3Storage

In this article

Short Description

Adds HPE 3PAR StoreServ storage systems to Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

This cmdlet provides parameter sets that allow you to:

* Add storage systems by user name and password.

|  |
| --- |
| Add-HP3Storage -Name <string> -UserName <string> -Password <string> [-Description <string>] [-Url <string>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-MountServer <CHost>] [-SkipRescan] [-Force] [-iSCSI] [-NFS] [-FibreChannel] [-NVMe] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRComputerFileProxyServer[]>] [-EnableVMwareBackup] [-EnableAgentBackup]   [<CommonParameters>] |

* Add storage systems by credentials.

|  |
| --- |
| Add-HP3Storage -Name <string> -Credentials <CInternalCredentials> [-Description <string>] [-Url <string>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-MountServer <CHost>] [-SkipRescan] [-Force] [-iSCSI] [-NFS] [-FibreChannel] [-NVMe] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRComputerFileProxyServer[]>] [-EnableVMwareBackup] [-EnableAgentBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet adds selected HPE 3PAR StoreServ storage systems to backup infrastructure.

When you add storage systems to your backup infrastructure, Veeam Backup & Replication performs a rescan of storage systems. During the rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

For more information about the rescan, see the [Adding Storage Systems](https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_add_storage.html?ver=13) section of the User Guide.

|  |
| --- |
| ![Add-HP3Storage](images/icon_tip.webp) Tip: |
| Use the SkipRescan parameter to skip the automatic rescan.  To rescan storage systems manually, use the following cmdlets:   * Run the [Sync-HP3Storage](sync-hp3storage.md) cmdlet to rescan of the entire storage system. * Run the [Sync-HP3Volume](sync-hp3volume.md) cmdlet to rescan selected HPE 3PAR StoreServ volumes added to backup infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Name | Specifies the storage IP address or DNS name. | String | True | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| Url | Specifies the HPE 3PAR Web Services API URL.  The HPE 3PAR Web Services API delivers a programming interface for performing storage management tasks with HPE 3PAR StoreServ storage systems. | String | False | Named | False |
| MountServer | Specifies the mount server that you want to use to work with this storage. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| WindowsMountServer | Specifies Windows mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| LinuxMountServer | Specifies Linux mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add an HPE 3PAR StoreServ storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableVMwareBackup | Enables the VMware backup option.  If you provide this parameter, you will be able to use storage snapshots to backup and restore VMware vSphere VMs hosted on storage systems. | SwitchParameter | False | Named | False |
| EnableAgentBackup | Enables the Veeam Agent backup option.  If you provide this parameter, you will be able to integrate your storage systems with Veeam Agent for Microsoft Windows installed on computers in your infrastructure. | SwitchParameter | False | Named | False |
| Proxy | For the EnableVMwareBackup parameter.  Specifies the array of proxies you want to use with this storage.  If set, Veeam Backup & Replication will use the selected proxies. If not set, Veeam Backup & Replication will use automatic proxy selection. | IProxy | False | Named | False |
| iSCSI | For the EnableVMwareBackup parameter.  Defines that the storage works over iSCSI protocol. | SwitchParameter | False | Named | False |
| NFS | For the EnableVMwareBackup parameter.  Defines that the storage works over NFS protocol. | SwitchParameter | False | Named | False |
| FibreChannel | For the EnableVMwareBackup parameter.  Defines that the storage works over FibreChannel protocol. | SwitchParameter | False | Named | False |
| NVMe | For the EnableVMwareBackup parameter. Defines that the storage works over the NVMe protocol. | SwitchParameter | False | Named | False |
| AgentFC | For the EnableAgentBackup parameter.  Defines that the storage works over FC protocol. | SwitchParameter | False | Named | False |
| AgentISCSI | For the EnableAgentBackup parameter.  Defines that the storage works over iSCSI protocol. | SwitchParameter | False | Named | False |
| AgentProxy | For the EnableAgentBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRComputerFileProxyServer object. To create this object, run the [Add-VBRComputerFileProxyServer](add-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Adding HPE 3PAR StoreServ Storage System

This example shows how to add a HPE 3PAR StoreServ storage system to the backup infrastructure using credentials.

|  |
| --- |
| $credentials = Get-VBRCredentials -Name "HPE 3PAR StoreServe Administrator"  $proxy = Get-VBRViProxy -Name 172.18.21.25  Add-HP3Storage -Name 172.18.44.8 -Credentials $credentials -Proxy $proxy -Description "HPE 3PAR StoreServe Storage" -Url https://172.18.44.8:8080 |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable.
2. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
3. Run the Add-HP3Storage cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $credentials variable as the Credentials parameter value.
* Set the $proxy variable as the Proxy parameter value.
* Specify the Description parameter value.
* Specify the Url parameter value.

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRViProxy](get-vbrviproxy.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
