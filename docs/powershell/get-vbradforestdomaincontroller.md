---
title: "Get-VBRADForestDomainController"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbradforestdomaincontroller.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRADForestDomainController


Short Description

Returns domain controllers for an Active Directory domain.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRADForestDomainController -ADForestDomain <VBRADForestDomain> [<CommonParameters>] |

Detailed Description

This cmdlet returns domain controllers that belong to the specified Active Directory domain.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| ADForestDomain | Specifies the Active Directory domain for which to return domain controllers. | Accepts the [VBRADForestDomain](vbradforestdomain.md) object. To get this object, run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestDomainController](vbradforestdomaincontroller.md)[] object that contains information about the domain controllers within an Active Directory domain.

Examples

Getting Domain Controllers for Active Directory Domain

This example shows how to get all domain controllers for an Active Directory domain.

|  |
| --- |
| $forest = Get-VBRADForest  $domain = Get-VBRADForestDomain -ADForest $forest  Get-VBRADForestDomainController -ADForestDomain $domain |

Perform the following steps:

1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable.
2. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domain variable.
3. Run the Get-VBRADForestDomainController cmdlet. Set the $domain variable as the ADForestDomain parameter value.

Related Commands

* [Get-VBRADForest](get-vbradforest.md)
* [Get-VBRADForestDomain](get-vbradforestdomain.md)

Page updated 2026-07-28

