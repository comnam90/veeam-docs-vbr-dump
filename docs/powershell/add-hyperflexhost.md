---
title: "Add-HyperFlexHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-hyperflexhost.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-HyperFlexHost

In this article

Short Description

Adds Cisco HyperFlex storage systems to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add storage systems by user name and password.

|  |
| --- |
| Add-HyperFlexHost -Name <string> -UserName <string> -Password <string> [-Description <string>] [-Proxy <IProxy[]>] [-Force] [-SkipRescan]  [<CommonParameters>] |

* Add storage systems by credentials.

|  |
| --- |
| Add-HyperFlexHost -Name <string> -Credentials <CInternalCredentials> [-Description <string>] [-Proxy <IProxy[]>] [-Force] [-SkipRescan]  [<CommonParameters>] |

Detailed Description

This cmdlet adds the Cisco HyperFlex storage systems to the backup infrastructure.

When you add storage systems to your backup infrastructure, Veeam Backup & Replication performs a rescan of storage systems. During the rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

For more information about the rescan, see the [Adding Storage Systems](https://helpcenter.veeam.com/docs/backup/vsphere/storage_configure_add_storage.html?ver=120) section of the User Guide for VMware vSphere.

|  |
| --- |
| Tip |
| Use the SkipRescan parameter to skip the automatic rescan.  To rescan storage systems manually, run the [Sync-HyperFlexHost](sync-hyperflexhost.md) cmdlet to rescan of the entire storage system. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the storage IP address or DNS name. | String | True | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | True | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| Proxy | Specifies the array of proxies you want to use with this storage. | Accepts the IProxy object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add a Cisco HyperFlex without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CCiscoHxHost object that defines settings of the HyperFlex storage systems added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Cisco HyperFlex Storage by Username and Password

|  |  |
| --- | --- |
| This command adds the 192.0.2.1 Cisco HyperFlex storage system by specifying user name and password.  |  | | --- | | Add-HyperFlexHost -Name 192.0.2.1 -UserName "Cisco HX Administrator" -Password "SecurePa$$w0rd" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Cisco HyperFlex Storage System Using Credentials

|  |  |
| --- | --- |
| This example shows how to add the 192.0.2.1 Cisco HyperFlex storage system to the backup infrastructure using the Cisco HX Administrator credentials.  |  | | --- | | $credentials = Get-VBRCredentials -Name "Cisco HX Administrator"  Add-HyperFlexHost -Name 192.0.2.1 -Credentials $credentials |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 2. Run the Add-HyperFlexHost cmdlet. Specify the Name parameter value. Set the $credentials variable as the Credentials parameter value. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRViProxy](get-vbrviproxy.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
