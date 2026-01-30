---
title: "Reset-VBRPluginCertificate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrplugincertificate.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Reset-VBRPluginCertificate


Short Description

Resets Veeam Plug-In SSL certificates.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VBRPluginCertificate -DiscoveredComputer <VBRDiscoveredComputer[]> -Type {OracleRMAN | SAPHANA | SAPOnOracle} [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet resets SSL certificates for selected Veeam Plug-Ins.

When you reset Veeam Plug-In certificates, all backup policies run by these Veeam Plug-Ins stop. You can use this cmdlet for performing Maintenance tasks on protected computers where the associated agents are installed.

Veeam Backup & Replication will regenerate a new SSL certificate automatically next time you run an application backup policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies the array of discovered computers. The cmdlet will reset SSL certificates for Veeam Agents installed on these computers.  Note: You can reset the SSL certificate only on discovered computers. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md)[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, |
| Type | Specifies the type of Veeam Plug-In to be installed on the protected computers:   * OracleRMAN: for Veeam Plug-In for Oracle RMAN * SAPHANA: for Veeam Plug-In for SAP HANA * SAPOnOracle: for Veeam Plug-In for SAP on Oracle | VBRApplicationType. | True | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Resetting SSL Certificates for Veeam Plug-In for Oracle RMAN Installed on Computers of Selected Protection Group

This example shows how to reset SSL certificates for Veeam Plug-In for Oracle RMAN installed on computers of the Database Servers protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Database Servers"  $discovered = Get-VBRDiscoveredApplication -ProtectionGroup $group  Reset-VBRPluginCertificate -Type OracleRMAN -DiscoveredComputer $discovered |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $discovered variable.
3. Run the Reset-VBRPluginCertificate cmdlet. Set the OracleRMAN option for the Type parameter. Set the $discovered variable as the DiscoveredComputer parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)


