---
title: "Find-VBRADEntity"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbradentity.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Find-VBRADEntity


Short Description

Looks for Active Directory objects.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Active Directory objects.

|  |
| --- |
| Find-VBRADEntity -Domain <VBRADDomain> [-Root <VBRADEntity>] [-Recurse]  [<CommonParameters>] |

* Get Active Directory objects by ID.

|  |
| --- |
| Find-VBRADEntity -Domain <VBRADDomain> [-Id <guid[]>] [-Root <VBRADEntity>] [-Recurse]  [<CommonParameters>] |

* Get Active Directory objects by name.

|  |
| --- |
| Find-VBRADEntity -Domain <VBRADDomain> [-Name <string[]>] [-Root <VBRADEntity>] [-Recurse]  [<CommonParameters>] |

* Get Active Directory objects of a specified type.

|  |
| --- |
| Find-VBRADEntity -Domain <VBRADDomain> [-Type <VBRADEntityType[]> {Domain | Cluster | OrganizationUnit | Group | Folder | Computer}] [-Root <VBRADEntity>] [-Recurse]  [<CommonParameters>] |

Detailed Description

This cmdlet looks for Active Directory objects.

You can use this cmdlet to search for Active Directory objects you plan to add to the scope of a protection group.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Domain | Specifies the Active Directory domain connection object. | Accepts the [VBRADDomain](vbraddomain.md) object. To get this object, run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Id | Specifies the array of object IDs. The cmdlet will return objects with these IDs. | Guid[] | False | Named | True (ByProperty Name) |
| Name | Specifies the array of object names. The cmdlet will return objects with these names. | String[] | False | Named | True (ByProperty Name) |
| Type | Specifies the array of object types:   * Domain * Cluster * OrganizationUnit * Group * Folder * Computer   The cmdlet will return objects of these types. | VBRADEntityType[] | False | Named | True (ByProperty Name) |
| Root | Specifies the container of objects. The cmdlet will look for objects in this container.  If omitted, the cmdlet will look for objects in the domain container. | Accepts the [VBRADEntity](vbradentity.md) object. To get this object, run the Find-VBRADEntity cmdlet. | False | Named | True (ByProperty Name) |
| Recurse | Defines that the cmdlet will look for objects from all child containers of the specified container. | SwitchParameter | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRADEntity](vbradentity.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active Directory Objects

|  |  |
| --- | --- |
| This example shows how to get all Active Directory objects.  |  | | --- | | $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  Find-VBRADEntity -Domain $connection -Recurse |  Perform the following steps:   1. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 2. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Active Directory Objects by Name

|  |  |
| --- | --- |
| This example shows how to get Active Directory objects with names containing account.  |  | | --- | | $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  Find-VBRADEntity -Domain $connection -Name \*account\* -Recurse |  Perform the following steps:   1. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 2. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Specify the Name parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Active Directory Objects from Container

|  |  |
| --- | --- |
| This example shows how to get Active Directory objects from the Accounts container.  |  | | --- | | $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  $root = Find-VBRADEntity -Domain $connection  $accounts = Find-VBRADEntity -Domain $connection -Root $root -Name Accounts  Find-VBRADEntity -Domain $connection -Root $accounts -Recurse |  Perform the following steps:   1. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 2. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Save the result to the $root variable. 3. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Set the $root variable as the Root parameter value. Specify the Name parameter value. Save the result to the $accounts variable. 4. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Set the $accounts variable as the Root parameter value. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Active Directory Objects by Type

|  |  |
| --- | --- |
| This example shows how to get all Active Directory objects of the OrganizationUnit type.  |  | | --- | | $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  Find-VBRADEntity -Domain $connection -Type OrganizationUnit -Recurse |  Perform the following steps:   1. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 2. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Set the OrganizationUnit option for the Type parameter. Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Active Directory Objects by ID

|  |  |
| --- | --- |
| This example shows how to get Active Directory objects by ID.  |  | | --- | | $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  Find-VBRADEntity -Domain $connection -Id 3826d21c-0f7d-4c80-b5ef-b5568e967a6a, 85950671-5e3a-481f-8408-5af40de317c6 |  Perform the following steps:   1. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 2. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value.  Specify the Id parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Getting Active Directory Object using Veeam PowerShell and Microsoft Active Directory Windows PowerShell

|  |  |
| --- | --- |
| This example shows how to get an Active Directory object using both Veeam PowerShell and [Microsoft Active Directory Windows PowerShell](https://technet.microsoft.com/en-us/library/dd378783%28WS.10%29.aspx) cmdlets.  |  | | --- | | $comp = Get-ADComputer SUPP-G3321  $compid = $comp.ObjectGUID  $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  Find-VBRADEntity -Domain $connection -Id $compid |  Perform the following steps:   1. Make sure you have the Active Directory Windows PowerShell module installed. For more information, see [Microsoft Docs](https://technet.microsoft.com/en-us/library/dd378783%28WS.10%29.aspx#Anchor_5). 2. Run the [Get-ADComputer](https://learn.microsoft.com/en-us/powershell/module/activedirectory/get-adcomputer?view=windowsserver2022-ps) to get the Active Directory computer. Save the result to the $comp variable. 3. Use the ObjectGUID property of the $comp variable. Save the result to the $compid variable. 4. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 5. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Set the $compid variable as the Id parameter value. |

Related Commands

[Get-VBRADDomain](get-vbraddomain.md)


