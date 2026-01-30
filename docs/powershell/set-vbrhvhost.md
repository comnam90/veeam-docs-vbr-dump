---
title: "Set-VBRHvHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvhost.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRHvHost


Short Description

Modifies settings of Hyper-V hosts.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify credentials of a Hyper-V host.

|  |
| --- |
| Set-VBRHvHost -Server <CHost> [-Description <String>] [-Credentials <CCredentials>]  [<CommonParameters>] |

* Modify account user name and password of a Hyper-V host.

|  |
| --- |
| Set-VBRHvHost -Server <CHost> [-User <String>] [-Password <String>] [-Description <String>]  [<CommonParameters>] |

* Modify authentication method of a Hyper-V host to the certificate-based authentication.

|  |
| --- |
| Set-VBRHvHost -Server <CHost> [-Description <String>] [-UseCertificate]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Hyper-V hosts.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the Hyper-V host which settings you want to modify. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Description | Specifies the description of the Hyper-V host. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Hyper-V host. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| User | Specifies the user name you want to use for authenticating with the Hyper-V host. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the Hyper-V host. | String | False | Named | False |
| UseCertificate | Defines that the cmdlet will use certificate-based authentication to authenticate with the Hyper-V host.  This authentication method requires Veeam Deployment Kit pre-installed on the target Hyper-V host. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the Hyper-V hosts added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying User Name and Password of Hyper-V Host

|  |  |
| --- | --- |
| This example shows how to modify the password of the account used to add the Hyper-V Exchange host Hyper-V cluster to the backup infrastructure.  |  | | --- | | $server = Get-VBRServer  Set-VBRHvHost Server $server -Password "XXXXXXXXXX" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable. 2. Run the Set-VBRHvHost cmdlet. Set the $server variable as the Server parameter value. Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Credentials of Hyper-V Host

|  |  |
| --- | --- |
| This example shows how to modify credentials of the HyperVExchange Hyper-V cluster.  |  | | --- | | $Administrator = Get-VBRCredentials  $server = Get-VBRServer  Set-VBRHvHost -Server $server -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable.  1. Run the Set-VBRHvHost cmdlet. Set the $server variable as the Server parameter value. Set the $Administrator variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Authentication Method of Hyper-V Host to Certificate-Based Authentication

|  |  |
| --- | --- |
| This example shows how to switch the authentication method of the HyperVExchange Hyper-V cluster to certificate-based authentication.  |  | | --- | | $server = Get-VBRServer  Set-VBRHvHost -Server $server -UseCertificate |  Perform the following steps:   1. Install Veeam Deployment Kit on the Hyper-V host you want to modify. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable. 3. Run the Set-VBRHvHost cmdlet. Set the $server variable as the Server parameter value. Provide the UseCertificate parameter. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)


