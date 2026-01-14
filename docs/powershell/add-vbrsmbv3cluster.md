---
title: "Add-VBRSmbV3Cluster"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrsmbv3cluster.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Add-VBRSmbV3Cluster

In this article

Short Description

Adds an SMB3 cluster to the backup infrastructure.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add an SMB3 cluster using the account user name and password.

|  |
| --- |
| Add-VBRSmbV3Cluster -Name <String> -User <String> -Password <String> [-Description <String>]  [<CommonParameters>] |

* Add an SMB3 cluster using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRSmbV3Cluster -Name <String> -Credentials <CCredentials> [-Description <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds an SMB3 cluster to the backup infrastructure.

Run the [Add-VBRSmbV3Host](add-vbrsmbv3host.md) cmdlet to add a standalone SMB3 server to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the full DNS name or IP address of the SMB3 cluster. | String | True | Named | False |
| User | Specifies the user name you want to use for authenticating with the SMB3 cluster. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the SMB3 cluster. | String | True | Named | False |
| Description | Specifies the description of the SMB3 cluster. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the SMB3 cluster. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New SMB3 Cluster Using User Name and Password

|  |  |
| --- | --- |
| This command adds a new SMB3 cluster named SMBCLUSTER01 with the Administrator user name and the qwerty password of the account. The description is Hyper-V SMB Share Cluster 01.  |  | | --- | | Add-VBRSmbV3Cluster -Name "SMBCLUSTER01" -User "Administrator" -Password "qwerty" -Description "Hyper-V SMB Share Cluster 01" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding New SMB3 Cluster Using Credentials

|  |  |
| --- | --- |
| This example shows how to add a new SMB3 cluster named SMBCLUSTER01 using credentials. The description is Hyper-V SMB Share Cluster 01.  |  | | --- | | $Administrator = Get-VBRCredentials  Add-VBRSmbV3Cluster -Name "SMBCLUSTER01" -Description "Hyper-V SMB Share Cluster 01" -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRSmbV3Cluster cmdlet. Specify the Name parameter value. Specify the Description parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 10/4/2024

Page content applies to build 13.0.1.1071
