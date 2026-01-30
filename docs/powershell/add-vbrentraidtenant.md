---
title: "Add-VBREntraIDTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrentraidtenant.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Add-VBREntraIDTenant


Short Description

Adds a Microsoft Entra ID tenant to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a tenant with the help of an existing application using password-based authentication.

|  |
| --- |
| Add-VBREntraIDTenant [-Region <VBRAzureBlobRegionType>] [-Description <String>] -TenantId <String> -ApplicationId <String> -SecretKey <SecureString> -CacheRepository <CBackupRepository> [-ProtectedScope <VBREntraIDTenantProtectedScope[]>]  [<CommonParameters>] |

* Add a tenant with the help of an existing application using certificate-based authentication.

|  |
| --- |
| Add-VBREntraIDTenant [-Region <VBRAzureBlobRegionType>] [-Description <String>] -TenantId <String> -ApplicationId <String> -CertificatePath <String> [-Password <SecureString>] -CacheRepository <CBackupRepository> [-ProtectedScope <VBREntraIDTenantProtectedScope[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a tenant to the backup infrastructure.

|  |
| --- |
| Note |
| To add a tenant, you need an application already created in Entra ID. If you want to create an application automatically, add the tenant using the UI. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| TenantId | Specifies the ID of the tenant which you want to add to the backup infrastructure. The cmdlet will search for the application within this tenant. | String | True | Named | False |
| ApplicationId | Specifies the ID of an application. The cmdlet will use this application to access Entra ID resources. | String | True | Named | False |
| SecretKey | For the password-based authentication.  Specifies an application secret. The cmdlet will use this secret to authenticate to Entra ID. | SecureString | True | Named | False |
| CacheRepository | Specifies a cache repository. The cmdlet will use this repository to store temporary cache files for log processing. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| CertificatePath | For the certificate-based authentication.  Specifies the path to the certificate. The cmdlet will use this certificate to authenticate to Entra ID. | String | True | Named | False |
| Region | Specifies the region type where the tenant is located. | [VBRAzureBlobRegionType](enums.md#VBRAzureBlobRegionType) | False | Named | False |
| Description | Specifies the description for the tenant that you want to add. | String | False | Named | False |
| Password | For the certificate-based authentication.  Specifies the password that the cmdlet will use to authenticate to Entra ID. | SecureString | False | Named | False |
| ProtectedScope | Specifies the tenant protection scope.  Note: If you do not specify this parameter, the following tenant resources will be protected by default:   * Users * Groups * Roles * Administrative units * Applications | Accepts the VBREntraIDTenantProtectedScope object. To get this object, run the [New-VBREntraIDTenantProtectedScope](new-vbrentraidtenantprotectedscope.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIdTenant](vbrentraidtenant.md) object that contains settings of the added tenant.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Tenant Using Password-Based Authentication

|  |  |
| --- | --- |
| This example shows how to add an Entra ID tenant using the password-based authentication.  |  | | --- | | $tenantId = "xxxxx"  $appId = "xxxxx"  $appSecret = Read-Host -Prompt "Enter password" -AsSecureString  $repo = Get-VBRBackupRepository -Name "Default Backup Repository"  $scope = New-VBREntraIDTenantProtectedScope -ResourceType Users, Groups, AdminUnits, ConditionalAccessPolicies  $tenant = Add-VBREntraIdTenant -TenantId $tenantId -ApplicationId $appId -SecretKey $appSecret -CacheRepository $repo -ProtectedScope $scope |  Perform the following steps:   1. Create the $tenantId and $appId variables whose values are the Entra ID tenant ID and the application ID. 2. Create the $appSecret variable. Use the Read-Host cmdlet to get the application secret and convert it to a secure string. 3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repo variable. 4. Run the [New-VBREntraIDTenantProtectedScope](new-vbrentraidtenantprotectedscope.md) cmdlet. Specify the ResourceType parameter value. Save the result to the $scope variable. 5. Run the Add-VBREntraIdTenant cmdlet. Specify the following settings:  * Set the $tenantId variable as the TenantId parameter value. * Set the $appId variable as the ApplicationId parameter value. * Set the $appSecret variable as the SecretKey parameter value. * Set the $repo variable as the CacheRepository parameter value. * Set the $scope variable as the ProtectedScope parameter value. * Save the result to the $tenant variable to be used with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Tenant Using Certificate-Based Authentication

|  |  |
| --- | --- |
| This example shows how to add an Entra ID tenant using the certificate-based authentication.  |  | | --- | | $tenantId = "xxxxx"  $appId = "xxxxx"  $psswd = Read-Host -Prompt "Enter password" -AsSecureString  $repo = Get-VBRBackupRepository -Name "Default Backup Repository"  $tenant = Add-VBREntraIdTenant -TenantId $tenantId -ApplicationId $appId -CertificatePath "C:\Users\Administrator\Locked\certificate-3518.pfx" -Password $psswd -CacheRepository $repo |  Perform the following steps:   1. Create the $tenantId and $appId variables whose values are the Entra ID tenant ID and the application ID. 2. Create the $psswd variable. Use the Read-Host cmdlet to get the password and convert it to a secure string. 3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repo variable. 4. Run the Add-VBREntraIdTenant cmdlet. Specify the following settings:  * Set the $tenantId variable as the TenantId parameter value. * Set the $appId variable as the ApplicationId parameter value. * Specify the CertificatePath parameter value. * Set the $psswd variable as the Password parameter value. * Set the $repo variable as the CacheRepository parameter value.  * Save the result to the $tenant variable to be used with other cmdlets. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBREntraIDTenantProtectedScope](new-vbrentraidtenantprotectedscope.md)


