---
title: "Add-VBRHvScvmm"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvscvmm.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Add-VBRHvScvmm


Short Description

Adds a Hyper-V SCVMM server to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a Hyper-V SCVMM server using the account user name and password.

|  |
| --- |
| Add-VBRHvScvmm -Name <String> -User <String> -Password <String> [-Description <String>]  [<CommonParameters>] |

* Add a Hyper-V SCVMM server using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRHvScvmm -Name <String> -Credentials <CCredentials> [-Description <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a Hyper-V SCVMM (Microsoft System Center Virtual Machine Manager) server to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the DNS name of the added SCVMM server. | String | True | Named | False |
| User | Specifies the user name you want to use for authenticating with the SCVMM server. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the SCVMM server. | String | True | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the SCVMM server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet | True | Named | False |
| Description | Specifies the description of the SCVMM server. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the Hyper-V SCVMM server added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding SCVMM Server Using Account User Name and Password

|  |  |
| --- | --- |
| This command adds the SCVMM1 SCVMM server with the Administrator user name and the qwerty password of the account.  |  | | --- | | Add-VBRHvScvmm -Name "SCVMM1" -User "Administrator" -Password "qwerty" -Description "SCVMM Server" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding SCVMM Server Using Credentials Managed by Veeam Backup & Replication

|  |  |
| --- | --- |
| This example shows how to add the SCVMM1 SCVMM server using the credentials managed by Veeam Backup & Replication.  |  | | --- | | $Administrator = Get-VBRCredentials  Add-VBRHvScvmm -Name "SCVMM1" -Description "SCVMM Server" -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRHvScvmm cmdlet. Specify the Name parameter value. Specify the Description parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


