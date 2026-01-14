---
title: "Set-VBREntraIDTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrentraidtenant.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Set-VBREntraIDTenant

In this article

Short Description

Modifies a Microsoft Entra ID tenant added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Change tenant settings and the current authentication for the password-based authentication.

|  |
| --- |
| Set-VBREntraIDTenant -Tenant <VBREntraIDTenant> [-Description <String>] -ApplicationId <String> -SecretKey <SecureString> -CacheRepository <CBackupRepository> [-ProtectedScope <VBREntraIDTenantProtectedScope[]>]  [<CommonParameters>] |

* Change tenant settings and the current authentication for the certificate-based authentication.

|  |
| --- |
| Set-VBREntraIDTenant -Tenant <VBREntraIDTenant> [-Description <String>] -ApplicationId <String> -CertificatePath <String> [-Password <SecureString>] -CacheRepository <CBackupRepository> [-ProtectedScope <VBREntraIDTenantProtectedScope[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an Entra ID tenant added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies the Entra ID tenant that you want to change. | Accepts the VBREntraIDTenant object. To get this object, run the [Get-VBREntraIDTenant](get-vbrentraidtenant.md) cmdlet. | True | Named | False |
| ApplicationId | Specifies the ID of an application. The cmdlet will use this application to access Entra ID resources. | String | True | Named | False |
| SecretKey | For the password-based authentication.  Specifies an application secret. The cmdlet will use this secret to authenticate to Entra ID. | SecureString | True | Named | False |
| CacheRepository | Specifies a cache repository. The cmdlet will use this repository to store temporary cache files for log processing. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| CertificatePath | For the certificate-based authentication.  Specifies the path to the certificate. The cmdlet will use this certificate to authenticate to Entra ID. | String | True | Named | False |
| Description | Specifies the description for the tenant that you want to add. | String | False | Named | False |
| Password | For the certificate-based authentication.  Specifies the password that the cmdlet will use to authenticate to Entra ID. | SecureString | False | Named | False |
| ProtectedScope | Specifies the tenant protection scope.  Note: If you do not specify this parameter, the following tenant resources will be protected by default:   * Users * Groups * Roles * Administrative units * Applications | Accepts the VBREntraIDTenantProtectedScope object. To get this object, run the [New-VBREntraIDTenantProtectedScope](new-vbrentraidtenantprotectedscope.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIdTenant](vbrentraidtenant.md) object that contains settings of the added tenant.

Examples

Modifying Entra ID Tenant

This example shows how to modify an Entra ID tenant and change the authentication method for the certificate-based authentication.

|  |
| --- |
| $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $psswd = Read-Host -Prompt "Enter password" -AsSecureString  $cacheRepo = Get-VBRBackupRepository -Name "Default Backup Repository"  $scope = New-VBREntraIDTenantProtectedScope -ResourceType Users, Groups, AdminUnits, ConditionalAccessPolicies  Set-VBREntraIdTenant -Tenant $tenant -ApplicationId $appId -CertificatePath "C:\Users\Administrator\Locked\certificate-3518.pfx" -Password $psswd -CacheRepository $cacheRepo -ProtectedScope $scope |

Perform the following steps:

1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable.
2. Create the $psswd variable. Use the Read-Host cmdlet to get the password and convert it to a secure string.
3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $cacheRepo variable.
4. Run the [New-VBREntraIDTenantProtectedScope](new-vbrentraidtenantprotectedscope.md) cmdlet. Specify the ResourceType parameter value. Save the result to the $scope variable.
5. Run the Set-VBREntraIdTenant cmdlet. Specify the following settings:

* Set the $tenant variable as the Tenant parameter value.
* Set the $appId variable as the ApplicationId parameter value.
* Specify the CertificatePath parameter value.
* Set the $psswd variable as the Password parameter value.
* Set the $cacheRepo variable as the CacheRepository parameter value.
* Set the $scope variable as the ProtectedScope parameter value.

Related Commands

* [Get-VBREntraIdTenant](get-vbrentraidtenant.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

* [New-VBREntraIDTenantProtectedScope](new-vbrentraidtenantprotectedscope.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
