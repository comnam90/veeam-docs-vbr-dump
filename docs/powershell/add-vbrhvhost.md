---
title: "Add-VBRHvHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvhost.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Add-VBRHvHost


Short Description

Adds Hyper-V hosts to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a Hyper-V host using the account user name and password.

|  |
| --- |
| Add-VBRHvHost -Name <String> -User <String> -Password <String> [-Description <String>]  [<CommonParameters>] |

* Add a Hyper-V host using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRHvHost -Name <String> [-Description <String>] -Credentials <CCredentials>  [<CommonParameters>] |

* Add a Hyper-V host using certificate-based authentication.

|  |
| --- |
| Add-VBRHvHost -Name <String> [-Description <String>] [-UseCertificate]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a Hyper-V host to the backup infrastructure.

If a Hyper-V host is part of a cluster, add the Hyper-V cluster instead of standalone Hyper-V host.

Run the [Add-VBRHvCluster](add-vbrhvcluster.md) cmdlet to add a Hyper-V cluster.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the DNS name of the Hyper-V host. | String | True | Named | False |
| User | Specifies the user name you want to use for authenticating with the Hyper-V host. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the Hyper-V host. | String | True | Named | False |
| Description | Specifies the description of the Hyper-V host. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Hyper-V host. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| UseCertificate | Defines that the cmdlet will use certificate-based authentication to authenticate with the Hyper-V host.  This authentication method requires Veeam Deployment Kit pre-installed on the target Hyper-V host. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the Hyper-V hosts added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New Hyper-V Host Using User Name and Password

|  |  |
| --- | --- |
| This command adds a new Hyper-V host named HyperVExchange with the Administrator user name and the qwerty password of the account. The description is Hyper-V Exchange host.  |  | | --- | | Add-VBRHvHost -Name "HyperVExchange" -User "Administrator" -Password "qwerty" -Description "Hyper-V Exchange host" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding New Hyper-V Host Using Credentials

|  |  |
| --- | --- |
| This example shows how to add a new Hyper-V host named HyperVExchange using credentials. The description is Hyper-V Exchange host.  |  | | --- | | $Administrator = Get-VBRCredentials  Add-VBRHvHost -Name "HyperVExchange" -Credentials $Administrator -Description "Hyper-V Exchange host" |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRHvHost cmdlet. Specify the Name parameter value. Set the $Administrator variable as the Credentials parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding New Hyper-V Host Using Certificate-Based Authentication

|  |  |
| --- | --- |
| This example shows how to add a new Hyper-V host named HyperVExchange using a certificate. The description is Hyper-V Exchange host.  |  | | --- | | Add-VBRHvHost -Name "HyperVExchange" -Description "Hyper-V Exchange host" -UseCertificate |  Perform the following steps:   1. Install Veeam Deployment Kit on the target Hyper-V host. 2. Run the Add-VBRHvHost cmdlet. Specify the Name and the Description parameter values. Provide the UseCertificate parameter. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


