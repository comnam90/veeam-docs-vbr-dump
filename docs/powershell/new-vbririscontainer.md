---
title: "New-VBRIrisContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbririscontainer.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRIrisContainer


Short Description

Defines containers of InterSystems IRIS servers for protection groups.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRIrisContainer -Credentials <VBRIndividualComputerCustomCredentials[]>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRIrisContainer](vbririscontainer.md) object that contains InterSystems IRIS servers added by custom credentials.

Use this object to add a protection group of InterSystems IRIS servers with the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Credentials | Specifies the credentials to authenticate against the InterSystems IRIS servers that you want to add to the container. | Accepts the VBRIndividualComputerCustomCredentials[] object. To create this object, run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRIrisContainer](vbririscontainer.md) object that contains InterSystems IRIS servers.

Examples

Creating an InterSystems IRIS Container

This example shows how to create a container of InterSystems IRIS servers.

|  |
| --- |
| $creds = Get-VBRCredentials -Name "iris\\administrator"  $customCreds = New-VBRIndividualComputerCustomCredentials -HostName "172.18.21.25" -Credentials $creds  $container = New-VBRIrisContainer -Credentials $customCreds |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable.
2. Run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. Save the result to the $customCreds variable.
3. Run the New-VBRIrisContainer cmdlet. Set the $customCreds variable as the Credentials parameter value. Save the result to the $container variable to use with other cmdlets.

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md)

Page updated 2026-06-18

