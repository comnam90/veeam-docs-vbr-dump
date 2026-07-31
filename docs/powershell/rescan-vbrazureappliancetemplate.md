---
title: "Rescan-VBRAzureApplianceTemplate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/rescan-vbrazureappliancetemplate.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Rescan-VBRAzureApplianceTemplate


Short Description

Rescans the Azure Backup Appliance template in the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Rescan-VBRAzureApplianceTemplate -TemplateOptions <VBRAzureApplianceTemplateDeploymentOptions[]> [<CommonParameters>] |

Detailed Description

This cmdlet rescans the Azure Backup Appliance template to update its settings in the backup infrastructure.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| TemplateOptions | Specifies options for the Azure Backup Appliance templates that you want to rescan. | Accepts the VBRAzureApplianceTemplateDeploymentOptions[] object. To create this object, run the [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRAzureApplianceTemplate](vbrazureappliancetemplate.md) object that contains settings of the rescanned Azure Backup Appliance template.

Examples

Rescanning Azure Backup Appliance Template

This example shows how to rescan an Azure Backup Appliance template.

|  |
| --- |
| $template = Get-VBRAzureApplianceTemplate -Name "MyApplianceTemplate"  $options = New-VBRAzureApplianceTemplateDeploymentOptions -Template $template  Rescan-VBRAzureApplianceTemplate -TemplateOptions $options |

Perform the following steps:

1. Run the [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md) cmdlet. Specify the Name parameter value. Save the result to the $template variable.
2. Run the [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md) cmdlet. Set the $template variable as the Template parameter value. Save the result to the $options variable.
3. Run the Rescan-VBRAzureApplianceTemplate cmdlet. Set the $options variable as the TemplateOptions parameter value.

Related Commands

* [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md)
* [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md)

Page updated 2026-05-27

