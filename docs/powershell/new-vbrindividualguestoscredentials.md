---
title: "New-VBRIndividualGuestOSCredentials"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrindividualguestoscredentials.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRIndividualGuestOSCredentials


Short Description

Defines a user account that will be explicitly used to connect to specific machine guest OSes.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRIndividualGuestOSCredentials -IndividualMachine <Object> -MachineCredentials <CCredentials>  [<CommonParameters>] |

Detailed Description

This cmdlet defines a user account that will be explicitly used to connect to the specific machine guest OS. This account must have local Administrator privileges on this machine guest OS.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| IndividualMachine | Specifies a machine to which guest OS you want to connect. | Accepts the Object object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| MachineCredentials | Specifies credentials of a user account that the cmdlet will use to connect to a machine guest OS. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRIndividualGuestOSCredentials object that defines a user account that will be used to connect to the VM guest OS.

Examples

Defining User Account To Connect to VM Guest OS

This example shows how to use the CDP Admin user account to connect to the WinSrv2073 VM guest OS.

|  |
| --- |
| $vm = Find-VBRViEntity -Name "WinSrv2073"  $credentials = Get-VBRCredentials -Name "CDP Admin"  New-VBRIndividualGuestOSCredentials -IndividualMachine $vm -MachineCredentials $credentials |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable.
3. Run the New-VBRIndividualGuestOSCredentials cmdlet. Set the $vm variable as the IndividualMachine parameter value. Set the $credentials variable as the MachineCredentials parameter value.

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)

* [Get-VBRCredentials](get-vbrcredentials.md)


