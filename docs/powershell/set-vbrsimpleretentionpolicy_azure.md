---
title: "Set-VBRSimpleRetentionPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsimpleretentionpolicy_azure.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSimpleRetentionPolicy

In this article

Short Description

Modifies a retention policy for backup copy jobs that process backups stored on external repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSimpleRetentionPolicy -RetentionPolicy <VBRSimpleRetentionPolicy> [-RestorePoints <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a retention policy for backup copy jobs that process backups stored on external repositories.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RetentionPolicy | Specifies a retention policy for a backup copy job. The cmdlet will modify this policy. | Accepts the VBRSimpleRetentionPolicy object. To get this object, run the [Get-VBRRetentionPolicy](get-vbrretentionpolicy.md) cmdlet. | True | Named | True (ByValue) |
| RestorePoints | Specifies a number of restore points. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSimpleRetentionPolicy object that contains a retention policy for backup copy jobs that process backups stored on external repositories.

Examples

Modifying Retention Policy for Backup Copy Job

This example shows how to modify a retention policy for a backup copy job. The target backup repository will keep the last 5 restore points.

|  |
| --- |
| $job = Get-VBRJob -Name "EC2 BCJ 01"  $policy = Get-VBRRetentionPolicy -Job $job  Set-VBRSimpleRetentionPolicy -RetentionPolicy $policy -RestorePoints 5 |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Get-VBRRetentionPolicy](get-vbrretentionpolicy.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $policy variable.
3. Run the Set-VBRSimpleRetentionPolicy cmdlet. Set the $policy variable as the RetentionPolicy parameter value. Specify the RestorePoints parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRRetentionPolicy](get-vbrretentionpolicy.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
