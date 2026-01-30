---
title: "Set-VBRHvCluster"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvcluster.html"
last_updated: "7/25/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvCluster


Short Description

Modifies settings of a Hyper-V cluster.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify account user name and password of a Hyper-V cluster.

|  |
| --- |
| Set-VBRHvCluster -Server <CHost> [-Description <String>] [-Credentials <CCredentials>]  [<CommonParameters>] |

* Modify credentials of a Hyper-V cluster.

|  |
| --- |
| Set-VBRHvCluster -Server <CHost> [-User <String>] [-Password <String>] [-Description <String>]  [<CommonParameters>] |

Detailed Description

Modifies settings of a Hyper-V cluster.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Hyper-V cluster which settings you want to modify. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Description | Specifies the description of the Hyper-V cluster. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Hyper-V cluster. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet | False | Named | False |
| User | Specifies the user name you want to use for authenticating with the Hyper-V cluster. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the Hyper-V cluster. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the Hyper-V clusters added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Password of Hyper-V Cluster

|  |  |
| --- | --- |
| This example shows how to change the password of the account used to add the HYPCLUSTER01 Hyper-V cluster to the backup infrastructure.  |  | | --- | | $Administrator = Get-VBRCredentials  $server = Get-VBRServer  Set-VBRHvCluster -Password "XXXXXXX" -Server $server |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable. 3. Run the Set-VBRHvCluster cmdlet. Specify the Password parameter value. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Credentials of Hyper-V Cluster

|  |  |
| --- | --- |
| This example shows how  modify credentials of the HYPCLUSTER01 Hyper-V cluster.  |  | | --- | | $Administrator = Get-VBRCredentials  $server = Get-VBRServer  Set-VBRHvCluster -Server $server -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable.  1. Run the Set-VBRHvCluster cmdlet. Set the $server variable as the Server parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)


