---
title: "Add-VBRSmbV3Host"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrsmbv3host.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Add-VBRSmbV3Host

In this article

Short Description

Adds an SMB3 host to the backup infrastructure.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a SMB3 host using the account user name and password.

|  |
| --- |
| Add-VBRSmbV3Host -Name <String> -User <String> -Password <String> [-Description <String>]  [<CommonParameters>] |

* Add a SMB3 host using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRSmbV3Host -Name <String> [-Description <String>] -Credentials <CCredentials>  [<CommonParameters>] |

Detailed Description

This cmdlet adds an SMB3 host to the backup infrastructure.

If an SMB3 host is part of a cluster, add the SMB3 cluster instead of standalone SMB3 host.

Run the [Add-VBRSmbV3Cluster](add-vbrsmbv3cluster.md) cmdlet to add an SMB3 cluster.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the DNS name of the SMB3 host. | String | True | Named | False |
| User | Specifies the user name you want to use for authenticating with the SMB3 host. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the SMB3 host. | String | True | Named | False |
| Description | Specifies the description of the SMB3 host. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the SMB3 host. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New SMB3 Host Using User Name and Password

|  |  |
| --- | --- |
| This command adds a new SMB3 host named SMBShare010 with the Administrator user name and the qwerty password of the account. The description is Hyper-V SMB Share Host 01.  |  | | --- | | Add-VBRSmbV3Host -Name "SMBShare010" -User "Administrator" -Password "qwerty" -Description "Hyper-V SMB Share Host 010" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding New SMB3 Host Using Credentials

|  |  |
| --- | --- |
| This example shows how to add a new SMB3 host named SMBShare010 using credentials. The description is Hyper-V SMB Share Host 01.  |  | | --- | | $Administrator = Get-VBRCredentials  Add-VBRSmbV3Host -Name "SMBShare010" -Description "Hyper-V SMB Share Host 010" -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRSmbV3Host cmdlet. Specify the Name parameter value. Specify the Description parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 10/4/2024

Page content applies to build 13.0.1.1071
