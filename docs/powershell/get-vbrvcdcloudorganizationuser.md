---
title: "Get-VBRvCDCloudOrganizationUser"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcloudorganizationuser.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCloudOrganizationUser

In this article

Short Description

Returns Cloud Director user accounts.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRvCDCloudOrganizationUser [-Name <string[]>] [-vCDCloudProvider <VBRCloudProvider[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRvCDCloudOrganizationUser object that contains the details about Cloud Director user accounts added to your Organization. You can use this object to create new subtenants.

|  |
| --- |
| ![Get-VBRvCDCloudOrganizationUser ](images/icon_note.webp) Note: |
| Consider the following:   * You must add the Cloud Director users to the Cloud Director Organization in VMware Cloud Director beforehand. The user must not have the administrator role. * This cmdlet works for tenants only. * Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet with the OrganizationUser parameter to get the array of the Cloud Director users from the Cloud Provider side. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for the Cloud Director user account that you want to get. | String[] | False | Named | True (ByValue, |
| vCDCloudProvider | Specifies the service provider added to Veeam Backup & Replication. | Accepts the VBRCloudProvider[] object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | False | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Director User Accounts in Cloud Director Organization

|  |  |
| --- | --- |
| This example shows how to get all Cloud Director user accounts added to your Cloud Director Organization.  |  | | --- | | Get-VBRvCDCloudOrganizationUser | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Director User Account by Name

|  |  |
| --- | --- |
| This example shows how to get a Cloud Director user by name.  |  | | --- | | Get-VBRvCDCloudOrganizationUser -Name "vCDUser1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cloud Director User Account by Cloud Director Service Provider

|  |  |
| --- | --- |
| This example shows how to get a Cloud Director user by Cloud Director service provider.  |  | | --- | | $provider = Get-VBRCloudProvider -Name "vCDProvider"  Get-VBRvCDCloudOrganizationUser -vCDCloudProvider $provider -Name "vCDuser" |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $provider variable. 2. Run the Get-VBRvCDCloudOrganizationUser cmdlet. Set the $provider variable as the vCDCloudProvider parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRCloudProvider](get-vbrcloudprovider.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
