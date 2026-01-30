---
title: "Disable-VBRCDPPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcdppolicy.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRCDPPolicy


Short Description

Disables CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRCDPPolicy -Policy <VBRCDPPolicyBase[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Run the [Enable-VBRCDPPolicy](enable-vbrcdppolicy.md) cmdlet to enable CDP policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies an array of CDP policies.The cmdlet will disable these policies. | Accepts the VBRCDPPolicyBase[] object. To get this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling CDP Policies

This example shows how to disable CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on..

|  |
| --- |
| $policy = Get-VBRCDPPolicy  Disable-VBRCDPPolicy -Policy $policy |

Perform the following steps:

1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Save the result to the $policy variable.
2. Run the Disable-VBRCDPPolicy cmdlet. Set the $policy variable as the Policy parameter value.

Related Commands

[Get-VBRCDPPolicy](get-vbrcdppolicy.md)


