---
title: "Remove-VBRAzureApplianceTemplate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrazureappliancetemplate.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRAzureApplianceTemplate


Short Description

Removes deployed helper appliance templates.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRAzureApplianceTemplate -Template <VBRAzureApplianceTemplate[]> [<CommonParameters>] |

Detailed Description

This cmdlet removes deployed helper appliance templates from the backup infrastructure and Microsoft Azure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Template | Specifies an array of helper appliance templates that you want to remove. | Accepts the VBRAzureApplianceTemplate[] object. To get this object, run the [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md) cmdlet. | True | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

This example shows how to remove a helper appliance template.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $template = Get-VBRAzureApplianceTemplate -Subscription $subscription  Remove-VBRAzureApplianceTemplate -Template $template |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable.
3. Run the [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save it to the $template variable.
4. Run the Remove-VBRAzureApplianceTemplate cmdlet. Set the $template variable as the Template parameter value.

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md)


