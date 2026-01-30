---
title: "Deploy-VBRAzureApplianceTemplate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/deploy-vbrazureappliancetemplate.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# Deploy-VBRAzureApplianceTemplate


Short Description

Deploys a helper appliance template.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Deploy-VBRAzureApplianceTemplate -TemplateOptions <VBRAzureApplianceTemplateDeploymentOptions[]>  [<CommonParameters>] |

Detailed Description

This cmdlet deploys a helper appliance template.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| TemplateOptions | Specifies helper appliance template options. The cmdlet will deploy the helper appliance template with the specified options. | Accepts the VBRAzureApplianceTemplateDeploymentOptions[] object. To create this object, use the [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md) cmdlet. | True | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureApplianceTemplate](vbrazureappliancetemplate.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Deploying a Helper Appliance Template

|  |  |
| --- | --- |
| This example shows how to deploy a helper appliance template.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "swedencentral"  $templateOpt = New-VBRAzureApplianceTemplateDeploymentOptions -Subscription $subscription -Location $location  Deploy-VBRAzureApplianceTemplate -TemplateOptions $templateOpt |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $location variable. 4. Run the [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save it to the $templateOpt variable. 5. Run the Deploy-VBRAzureApplianceTemplate cmdlet. Set the $templateOpt variable as the TemplateOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Redeploying a Helper Appliance Template

|  |  |
| --- | --- |
| This example shows how to redeploy a helper appliance template. This redeploy deletes the old template and creates the same template anew. The redeploy is needed to get the latest guest OS updates for the helper appliance templates.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "swedencentral"  $oldTemplate = Get-VBRAzureApplianceTemplate -Location $location  $newTemplateOptions =  New-VBRAzureApplianceTemplateDeploymentOptions -Template $oldTemplate  Deploy-VBRAzureApplianceTemplate -TemplateOptions $newTemplateOptions |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $location variable. 4. Run the [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md) cmdlet. Set the $location variable as the Location parameter value. Save the result to the $oldTemplate variable. 5. Run the [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md) cmdlet. Set the $oldTemplate variable as the Template parameter value. Save it to the $newTemplateOptions variable. 6. Run the Deploy-VBRAzureApplianceTemplate cmdlet. Set the $newTemplateOptions variable as the TemplateOptions parameter value. |

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)
* [New-VBRAzureApplianceTemplateDeploymentOptions](new-vbrazureappliancetemplatedeploymentoptions.md)


