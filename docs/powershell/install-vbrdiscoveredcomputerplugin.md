---
title: "Install-VBRDiscoveredComputerPlugin"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/install-vbrdiscoveredcomputerplugin.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Install-VBRDiscoveredComputerPlugin

In this article

Short Description

Installs Veeam Plug-Ins on discovered computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Install-VBRDiscoveredComputerPlugin -DiscoveredComputer <VBRDiscoveredComputer[]> [-RunAsync] -Type {OracleRMAN | SAPHANA | SAPOnOracle} [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet installs Veeam Plug-Ins on discovered computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies the array of discovered computers. The cmdlet will install Veeam Agents on these computers. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md)[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | True (ByPropertyName) |
| Type | Specifies the type of Veeam Plug-In to be installed on the protected computers:   * OracleRMAN: for Veeam Plug-In for Oracle RMAN * SAPHANA: for Veeam Plug-In for SAP HANA * SAPOnOracle: for Veeam Plug-In for SAP on Oracle   The cmdlet will return discovered computers with applications of these types. | VBRApplicationType | True | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Installing Veeam Plug-In for Oracle RMAN on Discovered Computers for Specified Protection Group

This example shows how to install Veeam Plug-In for Oracle RMAN on discovered computers for the Database Servers protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Database Servers"  $computers = Get-VBRDiscoveredComputer -ProtectionGroup $group  Install-VBRDiscoveredComputerPlugin -DiscoveredComputer $computers -Type OracleRMAN |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $computers variable.
3. Run the Install-VBRDiscoveredComputerPlugin cmdlet. Set the $computers variable as the DiscoveredComputer parameter value. Set the OracleRMAN option for the Type parameter.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
