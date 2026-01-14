---
title: "Add-VBRNutanixHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnutanixhost.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VBRNutanixHost

In this article

Short Description

Adds Nutanix Files storage systems to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add Nutanix Files storage systems by user name and password.

|  |
| --- |
| Add-VBRNutanixHost -Name <string> -UserName <string> -Password <string> [-Description <string>] [-Port <int>] [-NASProxy <VBRNASProxyServer[]>] [-SkipRescan] [-Force] [-NASSMB] [-NASNFS] [-NASCreateRulesAutomatically]  [<CommonParameters>] |

* Add Nutanix Files storage systems by credentials.

|  |
| --- |
| Add-VBRNutanixHost -Name <string> -Credentials <CInternalCredentials> [-Description <string>] [-Port <int>] [-NASProxy <VBRNASProxyServer[]>] [-SkipRescan] [-Force] [-NASSMB] [-NASNFS] [-NASCreateRulesAutomatically]  [<CommonParameters>] |

Detailed Description

This cmdlet adds Nutanix Files storage systems to the backup infrastructure.

When you add storage systems to your backup infrastructure, Veeam Backup & Replication performs rescan of storage systems. During the rescan operation Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure. For more information about the rescan, see the [Adding Storage Systems](https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_add_storage.html?ver=13) section of the User Guide.

|  |
| --- |
| Tip: |
| Provide the SkipRescan parameter to skip the automatic rescan operation.  To rescan storage systems manually, use the following cmdlets:   * Run [Sync-VBRNutanixHost](sync-vbrnutanixhost.md) to rescan of the entire storage system. * Run [Sync-VBRNutanixVolume](sync-vbrnutanixvolume.md) to rescan Nutanix Files volumes added to backup infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a storage system IP address or DNS name. | String | True | Named | False |
| UserName | Specifies the user name that you want to use for authentication to the storage system. | String | True | Named | False |
| Password | Specifies the password you want to use for authentication to the storage system. | String | True | Named | False |
| Credentials | Specifies the credentials that you want to use for authentication to the storage system. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Description | Specifies a description of the storage system. | String | False | Named | False |
| Port | Specifies the port used to connect to the  storage system. | Int | False | Named | False |
| NASProxy | Specifies the array of proxies you want to use. | Accepts the VBRNASProxyServer object. To create this object, run the [Add-VBRNASProxyServer](add-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add the storage system without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| NASSMB | Defines that the storage system will work over the SMB protocol. | SwitchParameter | False | Named | False |
| NASNFS | Defines that the storage system will work over the NFS protocol. | SwitchParameter | False | Named | False |
| NASCreateRulesAutomatically | Defines that the cmdlet will allow Veeam Backup & Replication to automatically create required SMB and NFS export rules in the storage system.  If you provide this parameter, the rules will be created automatically in case the proxies are unavailable. If you do not provide the parameter and use the NFS protocol, the rules will not be created, and you must create the rules manually in the Nutanix Files storage system. For the SMB protocol, no actions are required. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the CNutanixHost object that defines the settings of a Nutanix Files storage system.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Nutanix Files Storage Systems by User Name and Password

|  |  |
| --- | --- |
| This command adds Nutanix Files storage systems by user name and password.  |  | | --- | | Add-VBRNutanixHost -Name 167.16.21.25 -UserName Administrator -Password XXXXXXXXXXX | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Nutanix Files Storage Systems by Credentials

|  |  |
| --- | --- |
| This example shows how to add Nutanix Files storage systems by credentials.  |  | | --- | | $credentials = Get-VBRCredentials -Name \*Administrator\*  Add-VBRNutanixHost -Name 167.16.21.25 -Credentials $credentials |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 2. Run the Add-VBRNutanixHost cmdlet. Specify the Name parameter value. Set the $credentials variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
