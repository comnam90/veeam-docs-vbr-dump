---
title: "Add-VBRESXi"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbresxi.html"
last_updated: "10/22/2024"
product_version: "13.0.1.1071"
---

# Add-VBRESXi

In this article

Short Description

Adds VMware ESXi hosts to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add VMware ESXi hosts using the account user name and password.

|  |
| --- |
| Add-VBRESXi -Name <String> -User <String> -Password <String> [-Port <Int32>] [-Description <String>] [-WhatIf] [-Confirm] [-Force]  [<CommonParameters>] |

* Add VMware ESXi hosts using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRESXi -Name <String> -Credentials <CCredentials> [-Port <Int32>] [-Description <String>] [-WhatIf] [-Confirm] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds VMware ESXi hosts to the backup infrastructure.

|  |
| --- |
| Note |
| If an ESXi host is a part of a vCenter Server, it is recommended to add the vCenter Server instead of a single ESXi host. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the full DNS name or IP address of the ESXi host. | String | True | 1 | False |
| User | Specifies the user name you want to use for authenticating with the ESXi host. | String | True | 2 | False |
| Password | Specifies the password you want to use for authenticating with the ESXi host. | String | True | 3 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the ESXi server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Port | Specifies the Web service port for connection to the ESXi host.  Default: 443. | Int32 | False | Named | False |
| Description | Specifies the description of the ESXi server. | String | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add VMware ESXi hosts without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the VMware ESXi hosts to the backup infrastructure

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding VMware ESXi Hosts Using Account User Name and Password

|  |  |
| --- | --- |
| This command adds the 172.16.11.188 ESXi host with the Administrator user name and the qwerty password of the account.  |  | | --- | | Add-VBRESXi –Name 172.16.11.188 –User Administrator –Password qwerty | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding VMware ESXi Hosts Using Credentials Managed by Veeam Backup & Replication

|  |  |
| --- | --- |
| This example shows how to add the 172.16.11.188 ESXi host using the credentials managed by Veeam Backup & Replication.  |  | | --- | | $Administrator = Get-VBRCredentials  Add-VBRESXi –Name 172.16.11.188 -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRESXi cmdlet. Specify the Name parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 10/22/2024

Page content applies to build 13.0.1.1071
