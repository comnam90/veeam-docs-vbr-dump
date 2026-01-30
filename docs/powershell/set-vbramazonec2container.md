---
title: "Set-VBRAmazonEC2Container"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbramazonec2container.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAmazonEC2Container


Short Description

Modifies a scope of Amazon EC2 instances, EC2 tags or AWS datacenters for a protection group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAmazonEC2Container -Container <VBRAmazonEC2Container> [-Region <VBRAmazonEC2Region>] [-Entity <Object[]>] [-ExcludeEntities] [-ExcludedEntity <Object[]>] [-AutoAssignIAMRole]  [<CommonParameters>] |

Detailed Description

Modifies a scope of Amazon EC2 instances, EC2 tags or AWS datacenters for a protection group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies a scope of the following entities that you want to modify:   * EC2 instances. * EC2 tags. * AWS datacenters. | Accepts the VBRAmazonEC2Container object. To create this object, run the [New-VBRAmazonEC2Container](new-vbramazonec2container.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Region | Specifies AWS Regions in which you want to deploy Veeam Agent on cloud machines. | Accepts the VBRAmazonEC2Region object. To create this object, run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| Entity | Specifies an array of the following entities that the cmdlet till add to a scope of a protection group:   * EC2 instances. * EC2 tags. * AWS datacenters. | Accepts the Object[] object. To get this object, run the following  cmdlets:   * [Get-VBRAmazonEC2VM](get-vbramazonec2vm.md) * [New-VBRAmazonEC2Tag](new-vbramazonec2tag.md) * [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) | False | Named | True (ByValue, ByPropertyName) |
| ExcludeEntities | Defines that the cmdlet will exclude EC2 instances from a scope of a protection group. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |
| ExcludedEntity | Specifies the following entities that you do not want  to add to a protection group:   * EC2 instances. * EC2 tags. * AWS datacenters. | Object[] | False | Named | True (ByValue, ByPropertyName) |
| AutoAssignIAMRole | Defines that the cmdlet will automatically set the IAM role with the AmazonSSMManagedInstanceCore policy to the EC2 instances that you want to back up.  If you do not provide this parameter, you will have to set the IAM role manually. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2Container](vbramazonec2container.md)

Examples

Modifying Scope of AWS Datacenters for Protection Group

This example shows how to modify the scope of AWS datacenters. The cmdlet will change the datacenter from eu-central-1 to eu-north-1.

|  |
| --- |
| $AWSaccount = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $datacenter = Get-VBRAmazonEC2Region -Account $AWSaccount -RegionType Global -Name "eu-central-1"  $container = New-VBRAmazonEC2Container -Region $AWSregion -Entity $datacenter  $DCNew = Get-VBRAmazonEC2Region -Account $AWSaccount -RegionType Global -Name "eu-north-1"  Set-VBRAmazonEC2Container -Container $container -Entity $DCNew |

Perform the following steps:

1. Define the AWS datacenter protection scope:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $AWSaccount variable.
2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $AWSaccount variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $datacenter variable.
3. Run the [New-VBRAmazonEC2Container](new-vbramazonec2container.md) cmdlet. Set the $AWSregion variable as the Region parameter value. Set the $datacenter variable as the Entity parameter value. Save the result to the $container variable.

1. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $AWSaccount variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $DCNew variable.

1. Run the Set-VBRAmazonEC2Container cmdlet. Set the $container variable as the Container parameter value. Set the $DCNew variable as the Entity parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)
* [New-VBRAmazonEC2Container](new-vbramazonec2container.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)


