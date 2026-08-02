---
title: "Get-VBRADForestDomainRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbradforestdomainrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRADForestDomainRestorePoint


Short Description

Returns restore points for an Active Directory domain.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Active Directory domain restore points using the domain.

|  |
| --- |
| Get-VBRADForestDomainRestorePoint -Domain <VBRADForestDomain> [<CommonParameters>] |

* Get Active Directory domain restore points using the domain controller.

|  |
| --- |
| Get-VBRADForestDomainRestorePoint -DomainController <VBRADForestDomainController> [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points that are available for the specified Active Directory domain or domain controller.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Domain | Specifies an Active Directory domain. The cmdlet will return restore points that contain the specified domain. | Accepts the [VBRADForestDomain](vbradforestdomain.md) object. To get this object, run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. | True | Named | True (ByValue) |
| DomainController | Specifies an Active Directory domain controller. The cmdlet will return restore points that contain the specified domain controller. | Accepts the [VBRADForestDomainController](vbradforestdomaincontroller.md) object. To get this object, run the [Get-VBRADForestDomainController](get-vbradforestdomaincontroller.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestDomainRestorePoint](vbradforestdomainrestorepoint.md)[] object that contains information about the restore point of the Active Directory domain.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Restore Points by Domain

|  |  |
| --- | --- |
| This example shows how to get restore points for an Active Directory domain.  |  | | --- | | $forest = Get-VBRADForest  $domain = Get-VBRADForestDomain -ADForest $forest  Get-VBRADForestDomainRestorePoint -Domain $domain |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domain variable. 3. Run the Get-VBRADForestDomainRestorePoint cmdlet. Set the $domain variable as the Domain parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Points by Domain Controller

|  |  |
| --- | --- |
| This example shows how to get restore points for a specific domain controller.  |  | | --- | | $forest = Get-VBRADForest  $domain = Get-VBRADForestDomain -ADForest $forest  $controller = Get-VBRADForestDomainController -ADForestDomain $domain  Get-VBRADForestDomainRestorePoint -DomainController $controller |  Perform the following steps:   1. Run the [Get-VBRADForest](get-vbradforest.md) cmdlet. Save the result to the $forest variable. 2. Run the [Get-VBRADForestDomain](get-vbradforestdomain.md) cmdlet. Set the $forest variable as the ADForest parameter value. Save the result to the $domain variable. 3. Run the [Get-VBRADForestDomainController](get-vbradforestdomaincontroller.md) cmdlet. Set the $domain variable as the ADForestDomain parameter value. Save the result to the $controller variable. 4. Run the Get-VBRADForestDomainRestorePoint cmdlet. Set the $controller variable as the DomainController parameter value. |

Related Commands

* [Get-VBRADForest](get-vbradforest.md)
* [Get-VBRADForestDomain](get-vbradforestdomain.md)
* [Get-VBRADForestDomainController](get-vbradforestdomaincontroller.md)

Page updated 2026-07-28

