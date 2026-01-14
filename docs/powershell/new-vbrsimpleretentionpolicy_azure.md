---
title: "New-VBRSimpleRetentionPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsimpleretentionpolicy_azure.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# New-VBRSimpleRetentionPolicy

In this article

Short Description

Creates a retention policy for backup copy jobs that process backups stored on external repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSimpleRetentionPolicy [-RestorePoints <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet specifies a retention policy for backup copy job that process backups stored on external repositories. Veeam Backup & Replication will keep regular backups on the target backup repository according to this policy.

|  |
| --- |
| ![New-VBRSimpleRetentionPolicy](images/icon_note.webp) Note: |
| Run the [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy.md) cmdlet to create the GFS retention policy for backup copy jobs. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoints | Specifies a number of restore points. Veeam Backup & Replication will keep the selected number of restore points on the target backup repository. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSimpleRetentionPolicy object that contains a retention policy for backup copy jobs that process backups stored on external repositories.

Examples

Creating Retention Policy for Backup Copy Job

This command creates a retention policy for a backup copy job. The target backup repository will keep the last 5 restore points.

|  |
| --- |
| New-VBRSimpleRetentionPolicy -RestorePoints 5 |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
