---
title: "Set-HyperFlexHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-hyperflexhost.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-HyperFlexHost

In this article

Short Description

Modifies Cisco HyperFlex storage settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-HyperFlexHost -Host <CCiscoHxHost> [-Name <string>] [-Description <string>] [-UserName <string>] [-Password <string>] [-Credentials <CInternalCredentials>] [-Proxy  <IProxy[]>] [-SkipRescan] [-Force] [-EnableProxyAutoSelection]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Cisco HyperFlex storage systems.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage you want to modify. | Accepts the CCiscoHxHost object. To get this object, run the [Get-HyperFlexHost](get-hyperflexhost.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name of the storage. | String | False | Named | False |
| Description | Specifies the description of the storage. | String | False | Named | False |
| UserName | Specifies the user name that you want to use for authenticating with the storage. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the storage. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the storage. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Proxy | Specifies the array of proxies you want to use to work with this storage. | Accepts the IProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| SkipRescan | Defines that the cmdlet will not start the storage rescan automatically after you add storage systems to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a Cisco HyperFlex without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableProxyAutoSelection | Enables automatic proxy selection. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CCiscoHxHost object that defines settings of the HyperFlex storage systems added to the backup infrastructure.

Examples

Modifying Cisco HyperFlex Storage Systems Credentials

This example shows how to modify Cisco HyperFlex credentials.

|  |
| --- |
| $host = Get-HyperFlexHost  $creds = Get-VBRCredentials  Set-HyperFlexHost -Host $host -Credentials $creds |

Perform the following steps:

1. Run the Get-HyperFlexHost cmdlet. Save the result to the $host variable.
2. Run the Get-VBRCredentials cmdlet. Save the result to the $creds variable.
3. Run the Set-HyperFlexHost cmdlet. Set the $host variable as the Host parameter value. Set the $creds variable as the Credentials parameter value.

Related Commands

* [Get-HyperFlexHost](get-hyperflexhost.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRViProxy](get-vbrviproxy.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
