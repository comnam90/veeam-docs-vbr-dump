---
title: "Add-VNXHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vnxhost.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VNXHost


Short Description

Adds Dell VNX storage systems to Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

This cmdlet provides parameter sets that allow you to:

* Add storage systems by user name and password.

|  |
| --- |
| Add-VNXHost  -UserName <String>  -Password <String>[-Type <VBRVNXHostType>] [-Name <String>] [-Description <String>] [-CredentialsScope <VBRVNXBlockCredentialsScope>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-SkipRescan] [-Force] [-iSCSI] [-NFS] [-FibreChannel] [-NVMe] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRComputerFileProxyServer[]>] [-EnableVMwareBackup] [-EnableAgentBackup]  [<CommonParameters>] |

* Add storage systems by credentials.

|  |
| --- |
| Add-VNXHost  -Credentials <CInternalCredentials> [-Type <VBRVNXHostType>] [-Name <String>] [-Description <String>][-CredentialsScope <VBRVNXBlockCredentialsScope>] [-Proxy <IProxy[]>] [-WindowsMountServer <CHost>] [-LinuxMountServer <CHost>] [-SkipRescan] [-Force] [-iSCSI] [-NFS] [-FibreChannel] [-NVMe] [-AgentFC] [-AgentISCSI] [-AgentProxy <VBRComputerFileProxyServer[]>] [-EnableVMwareBackup] [-EnableAgentBackup]  [<CommonParameters>]] |

Detailed Description

This cmdlet adds selected Dell VNX storage systems to backup infrastructure.

When you add storage systems to your backup infrastructure, Veeam Backup & Replication performs a rescan of storage systems. During the rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

For more information about the rescan, see the [Adding Storage Systems](https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_add_storage.html?ver=13) section of the User Guide.

|  |
| --- |
| ![Add-VNXHost](images/icon_tip.webp) Tip: |
| Use the SkipRescan parameter to skip the automatic rescan.  To rescan storage systems manually, use the following cmdlets:   * Run the [Sync-VNXHost](sync-vnxhost.md) cmdlet to rescan of the entire storage system. * Run the [Sync-VNXVolume](sync-vnxvolume.md) cmdlet to rescan selected Dell VNX volumes added to backup infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the type of the VNX storage:   * VNXFile * VNXBlock * VNXe * Unity | VBRVNXHostType | True | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| Name | Specifies the storage IP address or DNS name. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| CredentialsScope | Used to authenticate with the VNXBlock.  Specifies the credentials scope: Global, Local, LDAP. | VBRVNXBlockCredentialsScope | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a Dell VNX storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableVMwareBackup | Enables the VMware backup option.  If you provide this parameter, you will be able to use storage snapshots to backup and restore VMware vSphere VMs hosted on storage systems. | SwitchParameter | False | Named | False |
| EnableAgentBackup | Enables the Veeam Agent backup option.  If you provide this parameter, you will be able to integrate your storage systems with Veeam Agent for Microsoft Windows installed on computers in your infrastructure. | SwitchParameter | False | Named | False |
| Proxy | For the EnableVMwareBackup parameter.  Specifies the array of proxies you want to use with this storage.  If set, Veeam Backup & Replication will use the selected proxies. If not set, Veeam Backup & Replication will use automatic proxy selection. | Accepts the IProxy object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| WindowsMountServer | Specifies Windows mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| LinuxMountServer | Specifies Linux mount server. The storage systems will use this mount server for file-level and application items restore. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| NVMe | For the EnableVMwareBackup parameter. Defines that the storage works over the NVMe protocol. | SwitchParameter | False | Named | False |
| iSCSI | For the EnableVMwareBackup parameter.  Defines that the storage works over iSCSI protocol. | SwitchParameter | False | Named | False |
| NFS | For the EnableVMwareBackup parameter.  Defines that the storage works over NFS protocol. | SwitchParameter | False | Named | False |
| FibreChannel | For the EnableVMwareBackup parameter.  Defines that the storage works over FibreChannel protocol. | SwitchParameter | False | Named | False |
| AgentFC | For the EnableAgentBackup parameter.  Defines that the storage works over the FC protocol. | SwitchParameter | False | Named | False |
| AgentISCSI | For the EnableAgentBackup parameter.  Defines that the storage works over the iSCSI protocol. | SwitchParameter | False | Named | False |
| AgentProxy | For the EnableAgentBackup parameter.  Specifies an array of proxies you want to use with this storage. | Accepts the VBRComputerFileProxyServer object. To create this object, run the [Add-VBRComputerFileProxyServer](add-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Adding VNX Storage System

This example shows how to add a Dell VNX storage system to the backup infrastructure using credentials.

|  |
| --- |
| $credentials = Get-VBRCredentials -Name "VNX Administrator"  $proxy = Get-VBRViProxy -Name 172.16.53.5  Add-VNXHost -Name 172.16.21.105 -Type VNXe -Credentials $credentials -Proxy $proxy -iSCSI |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable.
2. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
3. Run the Add-VNXHost cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the VNXe option for the Type parameter.
* Set the $credentials variable as the Credentials parameter value.
* Set the $proxy variable as the Proxy parameter value.
* Provide the iSCSI parameter.

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRViProxy](get-vbrviproxy.md)


