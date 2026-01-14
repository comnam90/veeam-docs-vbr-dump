---
title: "Get-VBRApplicationRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Get-VBRApplicationRestorePoint

In this article

Short Description

Returns restore points created with the VSS-aware image processing enabled.

Applies to

Platform: VMware, Hyper-V, Veeam Agent

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all restore points with VSS-aware image processing enabled.

|  |
| --- |
| Get-VBRApplicationRestorePoint  [<CommonParameters>] |

* Filter the restore points by name.

|  |
| --- |
| Get-VBRApplicationRestorePoint [-Name <String[]>]  [<CommonParameters>] |

* Filter the restore points by application.

|  |
| --- |
| Get-VBRApplicationRestorePoint [-Name <String[]>] [-Exchange] [-ActiveDirectory] [-SharePoint] [-Oracle] [-PostgreSQL] [-SQL] [-MongoDB] [<CommonParameters>] |

* Filter the restore points by ID.

|  |
| --- |
| Get-VBRApplicationRestorePoint [-Id <Guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of backups that were created with the VSS-aware image processing enabled.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a backed-up VM. The cmdlet will return the restore points created for this VM. | String[] | False | Named | False |
| Exchange | Defines that the cmdlet will return the restore points of Microsoft Exchange VMs. | SwitchParameter | False | Named | False |
| ActiveDirectory | Defines that the cmdlet will return the restore points of Microsoft Active Directory VMs. | SwitchParameter | False | Named | False |
| SharePoint | Defines that the the cmdlet will return the restore points of Microsoft SharePoint VMs. | SwitchParameter | False | Named | False |
| SQL | Defines that the the cmdlet will return the restore points of Microsoft SQL Server VMs. | SwitchParameter | False | Named | False |
| MongoDB | Defines that the the cmdlet will return the restore points of MongoDB VMs. | SwitchParameter | False | Named | False |
| Oracle | Defines that the the cmdlet will return the restore points of Oracle VMs. | SwitchParameter | False | Named | False |
| PostgreSQL | Defines that the the cmdlet will return the restore points of PostgreSQL VMs. | SwitchParameter | False | Named | False |
| Id | Filters the restore points by ID. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRApplicationRestorePoint](vbrapplicationrestorepoint.md)
* IVBRApplicationRestorePoint

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Returning all Restore Points

|  |  |
| --- | --- |
| This command returns all restore points of backups containing Microsoft SQL VMs.  |  | | --- | | Get-VBRApplicationRestorePoint -SQL | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Returning Specific Restore Point of Microsoft SQL VM

|  |  |
| --- | --- |
| This example shows how to return a specific restore points of a Microsoft SQL VM named crm\_db.  |  | | --- | | $crmdb = Get-VBRApplicationRestorePoint -SQL -Name "crm\_db"  $restorepoint = $crmdb[2] |  Perform the following steps:   1. Run the Get-VBRApplicationRestorePoint cmdlet. Provide the SQL parameter. Specify the Name parameter value. Save the result to the $crmdb variable. 2. Select the third restore point. Save the result to the $restorepoint variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Returning Most Recent Restore Point of Specific Microsoft SQL VM [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to return the most recent restore point of a Microsoft SQL VM named crm\_db.  |  | | --- | | $crmdb = Get-VBRApplicationRestorePoint -SQL -Name “CRM-db” | Sort-Object -Property CreationTime -Descending | Select-Object -First 1 |  Perform the following steps:   1. Run the Get-VBRApplicationRestorePoint cmdlet. Provide the SQL parameter. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Sort-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7.3&viewFallbackFrom=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 3. Pipe the cmdlet output to the [Select-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.3&viewFallbackFrom=powershell-7) cmdlet. Set the 1 number as the First parameter value. 4. Save the result to the $crmdb variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Looking for Specific Restore Point

|  |  |
| --- | --- |
| This command looks for a specific restore point with the 4d39c279-f15c-4fd3-9b32-5f4e65f221b2 Id.  |  | | --- | | Get-VBRApplicationRestorePoint -Id 4d39c279-f15c-4fd3-9b32-5f4e65f221b2 | |

Related Commands

* [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7)
* [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7)

Page updated 7/11/2024

Page content applies to build 13.0.1.1071
