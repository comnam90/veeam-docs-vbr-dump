---
title: "New-VBRADCustomCredentials"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbradcustomcredentials.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# New-VBRADCustomCredentials


Short Description

Specifies custom credentials for authenticating with Active Directory objects.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRADCustomCredentials -Entity <VBRADEntity> [-Credentials <CCredentials>]  [<CommonParameters>] |

Detailed Description

This cmdlet specifies custom credentials for authenticating with Active Directory objects you want to add to a protection group. Veeam Backup & Replication uses these credentials for Veeam Agent deployment and backup\restore activities.

By default, Veeam Backup & Replication uses Master account credentials for authenticating with all Active Directory objects in a protection group. For authenticating with Active Directory objects that require different credentials Veeam Backup & Replication uses custom credentials.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies Active Directory objects for which you want to specify custom credentials. | Accepts the [VBRADEntity](vbradentity.md) object. To get this object, run the [Find-VBRADEntity](find-vbradentity.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Credentials | Specifies custom credentials for authenticating with Active Directory objects in a protection group.  If not set, Veeam Backup & Replication will use Master account credentials for authenticating with associated objects.  Note: for string type, enter a user name in the DNS.DOMAIN.NAME\USERNAME or USERNAME@DNS.DOMAIN.NAME format. | Accepts string (user name) or the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRADCustomCredentials](vbradcustomcredentials.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Specifying Credentials for Authenticating with Active Directory Objects

|  |  |
| --- | --- |
| This example shows how to specify custom credentials for authenticating with Active Directory objects.  |  | | --- | | $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  $root = Find-VBRADEntity -Domain $connection  $accounts = Find-VBRADEntity -Domain $connection -Root $root -Name Accounts  $ccreds = Get-Credential  New-VBRADCustomCredentials -Entity $accounts -Credentials $ccreds |  Perform the following steps:   1. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 2. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Save the result to the $root variable. 3. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Set the $root variable as the Root parameter value. Specify the Name parameter value. Save the result to the $accounts variable. 4. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Type the credentials you want to use for authenticating with the Active Directory objects from the Accounts container. Save the result to the $ccreds variable. 5. Run the New-VBRADCustomCredentials cmdlet. Set the $accounts variable as the Entity parameter value. Set the $ccreds variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Specifying Master Account Credentials for Scope of Active Directory Objects

|  |  |
| --- | --- |
| This example shows how to specify Master account credentials for the scope of Active Directory objects.  |  | | --- | | $connection = Get-VBRADDomain -ServerName support.east -Credentials support\jsmith  $objects = Find-VBRADEntity -Domain $connection -Name Support  New-VBRADCustomCredentials -Entity $objects |  Perform the following steps:   1. Run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. Specify the ServerName and Credentials parameter values. Save the result to the $connection variable. 2. Run the Find-VBRADEntity cmdlet. Set the $connection variable as the Domain parameter value. Specify the Name parameter value. Save the result to the $objects variable. 3. Run the New-VBRADCustomCredentials cmdlet. Set the $objects variable as the Entity parameter value. |

Related Commands

* [Get-VBRADDomain](get-vbraddomain.md)
* [Find-VBRADEntity](find-vbradentity.md)


