---
title: "Add-VBRIsilonHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrisilonhost.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VBRIsilonHost

In this article

Short Description

Adds Dell PowerScale (formerly Isilon) storage systems to Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add storage systems by user name and password.

|  |
| --- |
| Add-VBRIsilonHost -Name <string> -UserName <string> -Password <string> [-Description <string>] [-Port <int>] [-NASProxy <VBRNASProxyServer[]>] [-SkipRescan] [-Force] [-NASSMB] [-NASNFS] [-NASCreateRulesAutomatically]  [<CommonParameters>] |

* Add storage systems by credentials.

|  |
| --- |
| Add-VBRIsilonHost -Name <string> -Credentials <CInternalCredentials> [-Description <string>] [-Port <int>] [-NASProxy <VBRNASProxyServer[]>] [-SkipRescan] [-Force] [-NASSMB] [-NASNFS] [-NASCreateRulesAutomatically]  [<CommonParameters>] |

Detailed Description

This cmdlet adds selected Dell PowerScale storage systems to the backup infrastructure.

When you add storage systems to your backup infrastructure, Veeam Backup & Replication performs a rescan of storage systems. During the rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

For more information about the rescan, see the [Adding Storage Systems](https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_add_storage.html?ver=13) section of the User Guide.

|  |
| --- |
| ![Add-VBRIsilonHost](images/icon_tip.webp) Tip: |
| Provide the SkipRescan parameter to skip the automatic rescan.  To rescan storage systems manually, use the following cmdlets:   * Run the [Sync-VBRIsilonHost](sync-vbrisilonhost.md) cmdlet to rescan of the entire storage system. * Run the [Sync-VBRIsilonVolume](sync-vbrisilonvolume.md) cmdlet to rescan selected Dell VNX volumes added to backup infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the storage IP address or DNS name. | String | True | Named | False |
| UserName | Specifies the user name that you want to use for authentication to the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| Port | Sets a port used to connect to the PowerScale storage. | Int | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a Dell PowerScale without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| NASProxy | Specifies the array of proxies you want to use. | Accepts the VBRNASProxyServer object. To create this object, run the [Add-VBRNASProxyServer](add-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| NASSMB | Defines that the storage will work over the SMB protocol. | SwitchParameter | False | Named | False |
| NASNFS | Defines that the storage will work over the NFS protocol. | SwitchParameter | False | Named | False |
| NASCreateRulesAutomatically | Defines that the cmdlet will allow Veeam Backup & Replication to automatically create required SMB and NFS export rules on the storage system.  If you provide this parameter, the rules will be created automatically in case the proxies are unavailable. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Dell PowerScale Storage by Username and Password

|  |  |
| --- | --- |
| This command adds the Isilon Administrator Dell PowerScale storage system by specifying user name and password.  |  | | --- | | Add-VBRIsilonHost -Name 172.16.21.105 -UserName "Isilon Administrator" -Password "SecurePa$$w0rd" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Dell PowerScale Storage System Using Credentials

|  |  |
| --- | --- |
| This example shows how to add the Isilon Administrator Dell PowerScale storage system to the backup infrastructure using credentials.  |  | | --- | | $credentials = Get-VBRCredentials -Name "Isilon Administrator"  Add-IsilonHost -Name 172.16.21.105 -Credentials $credentials -Proxy $proxy |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 2. Run the Add-IsilonHost cmdlet. Specify the Name parameter value. Set the $credentials variable as the Credentials parameter value. Set the $proxy variable as the Proxy parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
