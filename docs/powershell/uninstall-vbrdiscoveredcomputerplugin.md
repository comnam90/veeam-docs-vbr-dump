---
title: "Uninstall-VBRDiscoveredComputerPlugin"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrdiscoveredcomputerplugin.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Uninstall-VBRDiscoveredComputerPlugin

In this article

Short Description

Removes Veeam Plug-Ins from a specific protected computer.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRDiscoveredComputerPlugin -DiscoveredComputer <VBRDiscoveredComputer[]> -Type <VBRApplicationType> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Veeam Plug-Ins from a specific protected computer.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies an array of computers. The cmdlet will remove Veeam Plug-In from these computers. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md)[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Type | Specifies the type of Veeam Plug-In to be installed on the protected computers:   * OracleRMAN: for Veeam Plug-In for Oracle RMAN * SAPHANA: for Veeam Plug-In for SAP HANA * SAPOnOracle: for Veeam Plug-In for SAP on Oracle   The cmdlet will return discovered computers with applications of these types. | VBRApplicationType | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | True (ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Removing Veeam Plug-In from Protected Computers

This example shows how to remove Veeam Plug-In for Oracle RMAN from protected computers that are added to the specified protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Database Servers"  $computers = Get-VBRDiscoveredComputer -ProtectionGroup $group  Uninstall-VBRDiscoveredComputerPlugin -DiscoveredComputer $computers -Type OracleRMAN |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $computers variable.
3. Run the Uninstall-VBRDiscoveredComputerPlugin cmdlet. Set the $computers variable as the DiscoveredComputer parameter value. Set the OracleRMAN option for the Type parameter.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
