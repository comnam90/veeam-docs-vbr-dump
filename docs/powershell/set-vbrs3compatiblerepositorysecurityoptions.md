---
title: "Set-VBRS3CompatibleRepositorySecurityOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrs3compatiblerepositorysecurityoptions.html"
last_updated: "7/25/2024"
product_version: "13.0.1.1071"
---

# Set-VBRS3CompatibleRepositorySecurityOptions


Short Description

Modifies settings that Veeam Agent uses to access S3 compatible repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRS3CompatibleRepositorySecurityOptions -Repository <VBRAmazonS3CompatibleRepository> [-AccessControlPolicy <VBRS3CompatibleAccessControlPolicyType>] [-IAMEndpoint <String>] [-STSEndpoint <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings that Veeam Agent uses to access S3 compatible repositories.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an S3 compatible repository. The cmdlet will modify settings that Veeam Agent uses to access this repository. | Accepts the VBRAmazonS3CompatibleRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| AccessControlPolicy | Specifies how Veeam Agent accesses S3 compatible repositories:   * AllowAll — use this option if you want Veeam Agent to access S3 compatible directly using credentials for the S3 compatible bucket. * S3CompatibleManaged — use this option if you want Veeam Agent to access S3 compatible repositories directly using secure credentials with a service token. * VBRManaged — use this option if you want Veeam Agent to access S3 compatible repositories through gateway servers. | [VBRS3CompatibleAccessControlPolicyType](enums.md#VBRS3CompatibleAccessControlPolicyType) | False | Named | False |
| IAMEndpoint | For the direct secure connection with a service token.  Specifies an endpoint of your S3 compatible repository. The cmdlet will use this host to connect to this repository. | String | False | Named | False |
| STSEndpoint | For the direct secure connection with a service token.  Specifies the security token of your S3 compatible repository. The cmdlet will use this security token to connect to this repository. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRS3CompatibleRepositorySecurityOptions](vbrs3compatiblerepositorysecurityoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Direct Access to S3 Compatible Repositories [Using Bucket Credentials]

|  |  |
| --- | --- |
| This example shows how to set Veeam Agent to access S3 compatible repositories directly using credentials for the S3 compatible bucket.  |  | | --- | | $s3repository = Get-VBRObjectStorageRepository -Name "S3 Compatible Repository"  Set-VBRS3CompatibleRepositorySecurityOptions -Repository $s3repository -AccessControlPolicy AllowAll |  Perform the following steps:   1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $s3repository variable. 2. Run the Set-VBRS3CompatibleRepositorySecurityOptions cmdlet. Set the $s3repository variable as the Repository parameter value. Set the AllowAll option for the AccessControlPolicy parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Direct Access to S3 Compatible Repositories [Using Service Token]

|  |  |
| --- | --- |
| This example shows how to set Veeam Agent to access S3 compatible repositories directly. The cmdlet will connect to the iam.wasabisys.com  endpoint and will use secure credentials with the sts.wasabisys.com service token.  |  | | --- | | $s3repository = Get-VBRObjectStorageRepository -Name "S3 Compatible Repository"  Set-VBRS3CompatibleRepositorySecurityOptions -Repository $s3repository -AccessControlPolicy S3CompatibleManaged -IAMEndpoint "iam.wasabisys.com" -STSEndpoint "sts.wasabisys.com" |  Perform the following steps:   1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $s3repository variable.  1. Run the Set-VBRS3CompatibleRepositorySecurityOptions cmdlet. Specify the following settings:  * Set the $s3repository variable as the Repository parameter value. * Set the S3CompatibleManaged option for the AccessControlPolicy parameter. * Specify the IAMEndpoint parameter value. * Specify the STSEndpoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Setting Access Through Gateway Server to S3 Compatible Repositories

|  |  |
| --- | --- |
| This example shows how to set Veeam Agent to access S3 compatible repositories directly using credentials for the S3 compatible bucket.  |  | | --- | | $s3repository = Get-VBRObjectStorageRepository -Name "S3 Compatible Repository"  Set-VBRS3CompatibleRepositorySecurityOptions -Repository $s3repository -AccessControlPolicy VBRManaged |  Perform the following steps:   1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $s3repository variable. 2. Run the Set-VBRS3CompatibleRepositorySecurityOptions cmdlet. Set the $s3repository variable as the Repository parameter value. Set the VBRManaged option for the AccessControlPolicy parameter. |

Related Commands

[Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)


