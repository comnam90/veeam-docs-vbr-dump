---
title: "Get-VEADItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veaditem.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---

# Get-VEADItem


Short Description

Returns backed-up Active Directory objects.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Active Directory objects added to a specific container by the object ID or the object name.

|  |
| --- |
| Get-VEADItem [[-Name] <String>] [-Container] <VEADContainer> [-Recurse] [[-Id] <Guid>] [<CommonParameters>] |

* Get Active Directory objects added to a specific container by an LDAP query.

|  |
| --- |
| Get-VEADItem [-Container] <VEADContainer> [-LDAPQuery] <String> [<CommonParameters>] |

* Get Active Directory objects added to a specific domain by an LDAP query.

|  |
| --- |
| Get-VEADItem [-Domain] <VEADDomain> [-LDAPQuery] <String> [<CommonParameters>]>] |

Detailed Description

This cmdlet returns backed-up Active Directory objects.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies an Active Directory container. The cmdlet will return an array of objects added to this container. | Accepts the [VEADContainer](veadcontainer.md) object. To get this object, run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. | True | 0 | True (ByValue) |
| Domain | Specifies an Active Directory domain. The cmdlet will return an array of objects added to this domain. | Accepts the [VEADDomain](veaddomain.md) object. To get this object, run the [Get-VEADDomain](get-veaddomain.md) cmdlet. | True | 0 | True (ByValue) |
| LDAPQuery | Specifies an LDAP search query. The cmdlet will return Active Directory objects according to this query. | String | True | 1 | False |
| Id | Specifies an ID of an Active Directory object. The cmdlet will return Active Directory objects with the specified ID. | Guid | False | 1 | False |
| Name | Specifies a name of an Active Directory object. The cmdlet will return objects with the specified name. | String | False | 2 | False |
| Recurse | Defines that the cmdlet will return Active Directory objects with their child objects. For example, a Computer object can contain Shared Folder and Printer objects. | SwitchParameter | False | 3 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADItem](veaditem.md)[] array that contains Active Directory items.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active Directory Objects from Specific Container

|  |  |
| --- | --- |
| This example shows how to get all Active Directory objects from a specific parent container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  Get-VEADItem -Container $parentcontainer[3] |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the Get-VEADItem cmdlet. Set the $parentcontainer variable as the Container parameter value. Specify the ordinal number of the parent container. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Active Directory Object with Specific ID from Specific Container

|  |  |
| --- | --- |
| This example shows how to get an Active Directory object with a specific ID from a specific Active Directory container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  Get-VEADItem -Container $container -Id "2687bd4b-1028-47e7-b720-6bf065179452" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $container variable. 3. Run the Get-VEADItem cmdlet. Set the $container variable as the Container parameter value. Specify the Id parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Active Directory Objects with Specific Name from Specific Child Container

|  |  |
| --- | --- |
| This example shows how to get all Active Directory objects with a specific name from an Active Directory child container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain -Id 0486045e-b583-4559-a0ab-d78b99f1b95d  $childcontainer = Get-VEADContainer -Container $parentcontainer  Get-VEADItem -Container $childcontainer -Name "SalesMailbox" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Specify the Id parameter value. Save the result to the $parentcontainer variable. 3. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $parentcontainer variable as the Container parameter value. Save the result to the $childcontainer variable. 4. Run the Get-VEADItem cmdlet. Set the $childcontainer variable as the Container parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Active Directory Objects from Specific Container with LDAP Query

|  |  |
| --- | --- |
| This example shows how to use an LDAP query to get an Active Directory object from a specific Active Directory container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $container = Get-VEADContainer -Domain $domain  Get-VEADItem -Container $container -LDAPQuery "(cn=SalesMailboxe8e8782f639e4a24898b93c325d8ed9d)" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the [Get-VEADContainer](get-veadcontainer.md) cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $container variable. 3. Run the Get-VEADItem cmdlet. Set the $container variable as the Container parameter value. Specify the LDAPQuery parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Active Directory Objects from Specific Domain with LDAP Query

|  |  |
| --- | --- |
| This example shows how to use an LDAP query to get an Active Directory object from a specific domain.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  Get-VEADItem -Domain $domain -LDAPQuery "(cn=ISW12R2SP13)" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADItem cmdlet. Set the $domain variable as the Domain parameter value. Specify the LDAPQuery parameter value. |

Related Commands

* [Get-VEADRestoreSession](get-veadrestoresession.md)
* [Get-VEADDomain](get-veaddomain.md)
* [Get-VEADContainer](get-veadcontainer.md)


