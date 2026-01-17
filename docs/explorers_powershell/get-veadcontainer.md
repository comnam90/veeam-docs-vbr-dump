---
title: "Get-VEADContainer"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veadcontainer.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Get-VEADContainer


Short Description

Returns backed-up Active Directory containers.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Active Directory containers in a domain.

|  |
| --- |
| Get-VEADContainer [-Domain] <VEADDomain> [[-Name] <String>] [[-Id] <Guid>] [-Recurse] [[-Type] <VEADContainerType>] [<CommonParameters>] |

* Get Active Directory containers added to a parent container.

|  |
| --- |
| Get-VEADContainer [-Container] <VEADContainer> [[-Name] <String>] [[-Id] <Guid>] [-Recurse] [[-Type] <VEADContainerType>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up Active Directory containers. Use this object to restore Active Directory data.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Domain | Specifies an Active Directory domain. The cmdlet will return an array of containers that are available in this domain. | Accepts the [VEADDomain](veaddomain.md) object. To get this object, run the [Get-VEADDomain](get-veaddomain.md) cmdlet. | True | 0 | True (ByValue) |
| Container | Specifies a parent container. The cmdlet will return containers that are available in this parent container. | Accepts the [VEADContainer](veadcontainer.md) object. To get this object, run the Get-VEADContainer cmdlet. | True | 0 | True (ByValue) |
| Id | Specifies an ID of an Active Directory child container. The cmdlet will return the Active Directory child container with this ID. | Guid | False | 1 | False |
| Name | Specifies a name of an Active Directory child container. The cmdlet will return the Active Directory child container with this name. | String | False | 2 | False |
| Type | Specifies the type of Active Directory container that you want to get. You can specify one of the following types:   * UsersAndComputers * GroupPolicyObjects * IntegratedDNS * ConfigurationPartition * DfsConfiguration | VEADContainerType | False | 3 | False |
| Recurse | Defines that the cmdlet will look for objects from all Active Directory child containers. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADContainer](veadcontainer.md)[] array that contains Active Directory containers.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Active Directory Containers from Domain

|  |  |
| --- | --- |
| This example shows how to get top-level Active Directory containers that are added to a domain.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  Get-VEADContainer -Domain $domain |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADContainer cmdlet. Set the $domain variable as the Domain parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Active Directory Container with Specific Name from Domain

|  |  |
| --- | --- |
| This example shows how to get an Active Directory container with a specific name from a domain.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  Get-VEADContainer -Domain $domain -Name "Domain controller" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADContainer cmdlet. Set the $domain variable as the Domain parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Active Directory Container with Specific ID from Domain

|  |  |
| --- | --- |
| This example shows how to get an Active Directory container with a specific ID from a domain.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  Get-VEADContainer -Domain $domain -ID "4e9c3f01-1955-453d-b2fe-80656d891708" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADContainer cmdlet. Set the $domain variable as the Domain parameter value. Specify the ID parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Active Directory Containers from Parent Container

|  |  |
| --- | --- |
| This example shows how to get all Active Directory containers from an Active Directory parent container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  Get-VEADContainer -Container $parentcontainer[8] |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADContainer cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the Get-VEADContainer cmdlet. Set the $parentcontainer variable as the Container parameter value. Specify the ordinal number of the parent container. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Active Directory Containers with Specific Name from Parent Container

|  |  |
| --- | --- |
| This example shows how to get all Active Directory child containers with a specific name from an Active Directory parent container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  Get-VEADContainer -Container $parentcontainer[8] -Name "Sales Mailboxes" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADContainer cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the Get-VEADContainer cmdlet. Specify the following settings:  * Set the $parentcontainer variable as the Container parameter value. Specify the ordinal number of the parent container. * Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Getting Active Directory Container with Specific ID from Parent Container

|  |  |
| --- | --- |
| This example shows how to get an Active Directory child container with a specific ID from an Active Directory parent container.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  $parentcontainer = Get-VEADContainer -Domain $domain  Get-VEADContainer -Container $parentcontainer[8] -ID "1b12ab63-4fc2-485d-a350-f5430ddde767" |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADContainer cmdlet. Set the $domain variable as the Domain parameter value. Save the result to the $parentcontainer variable. 3. Run the Get-VEADContainer cmdlet. Specify the following settings:  * Set the $parentcontainer variable as the Container parameter value. Specify the ordinal number of the parent container. * Specify the Id parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Getting Active Directory Containers of Specific Type

|  |  |
| --- | --- |
| This example shows how to get all Active Directory containers of the Users And Computers type.  |  | | --- | | $session = Get-VEADRestoreSession  $domain = Get-VEADDomain -Session $session[3]  Get-VEADContainer -Domain $domain -Type UsersAndComputers |  Perform the following steps:   1. Run the [Get-VEADRestoreSession](get-veadrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Run the [Get-VEADDomain](get-veaddomain.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $domain variable. 2. Run the Get-VEADContainer cmdlet. Set the $domain variable as the Domain parameter value. Specify the Type parameter value. |

Related Commands

* [Get-VEADRestoreSession](get-veadrestoresession.md)

* [Get-VEADDomain](get-veaddomain.md)


