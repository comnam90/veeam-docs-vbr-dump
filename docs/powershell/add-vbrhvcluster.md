---
title: "Add-VBRHvCluster"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvcluster.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Add-VBRHvCluster

In this article

Short Description

Adds a Hyper-V cluster to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a Hyper-V cluster using the account user name and password.

|  |
| --- |
| Add-VBRHvCluster -Name <String> -User <String> -Password <String> [-Description <String>]  [<CommonParameters>] |

* Add a Hyper-V cluster using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRHvCluster -Name <String> -Credentials <CCredentials> [-Description <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds Hyper-V clusters to the backup infrastructure.

Run the [Add-VBRHvHost](add-vbrhvhost.md) cmdlet to add a standalone Hyper-V host to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the DNS name of the Hyper-V cluster. | String | True | Named | False |
| User | Specifies the user name you want to use for authenticating with the Hyper-V cluster. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the Hyper-V cluster. | String | True | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Hyper-V cluster. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet | True | Named | False |
| Description | Specifies the description of the Hyper-V cluster. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the Hyper-V clusters added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Hyper-V Cluster Using Account User Name and Password

|  |  |
| --- | --- |
| This command adds the HYPCLUSTER01 Hyper-V cluster server with the Administrator user name and the qwerty password of the account.  |  | | --- | | Add-VBRHvCluster -Name "HYPCLUSTER01" -User "Administrator" -Password "qwerty" -Description "Hyper-V Cluster 01" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Hyper-V Cluster Using Credentials Managed by Veeam Backup & Replication

|  |  |
| --- | --- |
| This example shows how to add the HYPCLUSTER01 Hyper-V server using the credentials managed by Veeam Backup & Replication.  |  | | --- | | $Administrator = Get-VBRCredentials  Add-VBRHvCluster -Name "HYPCLUSTER01" -Description "Hyper-V Cluster 01" -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRHvCluster cmdlet. Specify the Name parameter value. Specify the Description parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 10/4/2024

Page content applies to build 13.0.1.1071
