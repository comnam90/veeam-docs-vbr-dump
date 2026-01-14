---
title: "get-veadadcontainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veadadcontainer.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

This cmdlet returns Active Directory containers that are available on the target server.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEADADContainer -Server <string> -Credential <pscredential> [-UseSSL] [-Id <guid>] [-Name <string>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Active Directory containers that are available on the target server. You can restore Active Directory objects to these containers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies DNS name or IP address of the target server. Veeam Explorer for Microsoft Active Directory will restore Active Directory objects to the specified server. | String | True | Named | False |
| Credential | Specifies credential records that Veeam Explorer for Microsoft Active Directory will use to connect to an LDAP server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |
| UseSSL | Defines that Veeam Explorer for Microsoft Active Directory will establish a secure SSL connection to the target server.  If you provide this parameter, Veeam Explorer for Microsoft Active Directory will connect over SSL to the target server. Otherwise, Veeam Explorer for Microsoft Active Directory will connect to the target server using a non-secure connection. | SwitchParameter | False | Named | False |
| Id | Specifies an ID of the container. Veeam Explorer for Microsoft Active Directory will get the container with the specified ID. | Guid | False | Named | False |
| Name | Specifies a name of the container. Veeam Explorer for Microsoft Active Directory will get the container with the specified name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADADContainer](veadadcontainer.md)[] array that contains Active Directory containers available on the target server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Containers from Target Server

|  |  |
| --- | --- |
| This example shows how to get all containers that are available on the target server.  |  | | --- | | $credentials = Get-Credential  Get-VEADADContainer -Server 172.16.8.223 -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $credentials variable. 2. Run the Get-VEADADContainer cmdlet. Specify the Server parameter value. Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Container from Target Server by Container ID

|  |  |
| --- | --- |
| This example shows how to get the 0559b025-2c09-4f10-a6b5-3f497166d895 container from the target server.  |  | | --- | | $credentials = Get-Credential  Get-VEADADContainer -Server 172.16.8.223 -Credential $credentials -Id 0559b025-2c09-4f10-a6b5-3f497166d895 |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $credentials variable. 2. Run the Get-VEADADContainer cmdlet. Specify the following settings:  * Specify the Server parameter value. * Set the $credentials variable as the Credential parameter value. * Specify the Id parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Container from Target Server by Container Name

|  |  |
| --- | --- |
| This example shows how to get a container from the target server with a specific container name.  |  | | --- | | $credentials = Get-Credential  Get-VEADADContainer -Server 172.16.8.223 -Credential $credentials -Name "Domain Controllers" |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the target server. Save the result to the $credentials variable.  1. Run the Get-VEADADContainer cmdlet. Specify the following settings:  * Specify the Server parameter value. * Set the $credentials variable as the Credential parameter value. * Specify the Name parameter value. |

Related Commands

[Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
