---
title: "Add-VBRvCenter"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcenter.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Add-VBRvCenter


Short Description

Adds vCenter Servers to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add vCenter Servers using the account user name and password.

|  |
| --- |
| Add-VBRvCenter -Name <string> -User <string> -Password <string> [-Port <int>] [-Description <string>] [-WhatIf] [-Confirm] [-Force]  [<CommonParameters>] |

* Add vCenter Servers using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRvCenter -Name <string> -Credentials <CCredentials> [-Port <int>] [-Description <string>] [-WhatIf] [-Confirm] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to add a vCenter Server to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the full DNS name or IP address of the vCenter Server. | String | True | 1 | False |
| User | Specifies the user name that you want to use for authenticating with the vCenter Server.  Note: The user name must be in the DOMAIN\username format. | String | True | 2 | False |
| Password | Specifies the password you want to use for authenticating with the vCenter Server. | String | True | 3 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the vCenter Server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Port | Specifies the Web service port for connection to the vCenter Server.  Default: 443 | Int | False | Named | False |
| Description | Specifies the description of the vCenter Server. | String | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a vCenter Server without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding vCenter to Backup Infrastructure Using Account User Name and Password

|  |  |
| --- | --- |
| This command adds the vc25.domain.local vCenter Server. The user name is Domain\Administrator and the password is qwerty.  |  | | --- | | Add-VBRvCenter -Name "vc25.domain.local" -User "Domain\Administrator" -Password "qwerty" -Description "vcdev25 vCenter Server" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding vCenter to Backup Infrastructure Using Credentials Managed by Veeam Backup & Replication

|  |  |
| --- | --- |
| This example shows how to add the vc25.domain.local vCenter Server.  |  | | --- | | $vc\_administrator = Get-VBRCredentials  Add-VBRvCenter -Name "vc25.domain.local" -Description "vcdev25 vCenter Server" -Credentials $vc\_administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $vc\_administrator variable. 2. Run the Add-VBRvCenter cmdlet. Specify the following settings:  * Specify the Name parameter value. * Specify the Description parameter value. * Set the $vc\_administrator variable as the Credentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


