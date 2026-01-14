---
title: "Set-VBRHvScvmm"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvscvmm.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvScvmm

In this article

Short Description

Modifies settings of a Hyper-V SCVMM server.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modifies account user name and password of a Hyper-V SCVMM server.

|  |
| --- |
| Set-VBRHvScvmm -Server <CHost> [-Description <String>] [-Credentials <CCredentials>]  [<CommonParameters>] |

* Modifies credentials of a Hyper-V SCVMM server.

|  |
| --- |
| Set-VBRHvScvmm -Server <CHost> [-User <String>] [-Password <String>] [-Description <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a Hyper-V SCVMM server.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Hyper-V SCVMM server which settings you want to modify. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Description | Specifies the description of the SCVMM server. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the SCVMM server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet | False | Named | False |
| User | Specifies the user name you want to use for authenticating with the SCVMM server. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the SCVMM server. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the Hyper-V SCVMM server added to the backup infrastructure.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Password of Hyper-V SCVMM Server

|  |  |
| --- | --- |
| This example shows how to change the password of the account used to add the Hyper-V SCVMM server to the backup infrastructure.  |  | | --- | | $Administrator = Get-VBRCredentials  $server = Get-VBRServer  Set-VBRHvScvmm -Password "XXXXXXX" -Server $server |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable. 3. Run the Set-VBRHvScvmm cmdlet. Specify the Password parameter value. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Credentials of Hyper-V SCVMM Server

|  |  |
| --- | --- |
| This example shows how to modify credentials of the Hyper-V SCVMM server.  |  | | --- | | $Administrator = Get-VBRCredentials  $server = Get-VBRServer  Set-VBRHvScvmm -Server $server -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable.  1. Run the Set-VBRHvScvmm cmdlet. Set the $server variable as the Server parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
