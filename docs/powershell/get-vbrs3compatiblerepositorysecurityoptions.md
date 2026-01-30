---
title: "Get-VBRS3CompatibleRepositorySecurityOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrs3compatiblerepositorysecurityoptions.html"
last_updated: "7/25/2024"
product_version: "13.0.1.1071"
---

# Get-VBRS3CompatibleRepositorySecurityOptions


Short Description

Returns settings that Veeam Agent uses to access S3 compatible repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRS3CompatibleRepositorySecurityOptions -Repository <VBRAmazonS3CompatibleRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet returns settings that Veeam Agent uses to access S3 compatible repositories. These settings contain the following information:

* The repository ID.
* The access control policy that specifies the Veeam Agent job mode:

* AllowAll — defines that Veeam Agent has a direct access to the S3 compatible repository. To authenticate against the repository, Veeam Agent uses credentials for the S3 compatible bucket.
* S3CompatibleManaged — defines that Veeam Agent has a direct access to the S3 compatible repository. To authenticate against the repository, Veeam Agent uses secure credentials with a service token.
* VBRManaged — defines that Veeam Agent accesses S3 compatible repositories through gateway servers.

* An endpoint that Veeam Agent uses to accesses S3 compatible repositories directly using secure credentials.
* A security token that Veeam Agent uses to accesses S3 compatible repositories directly using secure credentials.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an S3 compatible repository. The cmdlet will return settings that Veeam Agent uses to access S3 compatible repositories directly. | Accepts the VBRAmazonS3CompatibleRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRS3CompatibleRepositorySecurityOptions](vbrs3compatiblerepositorysecurityoptions.md)

Examples

Getting Access Settings for S3 Compatible Repositories

This example shows how to get settings that Veeam Agent uses to access the Repository 05 S3 compatible repository.

|  |
| --- |
| $s3repository = Get-VBRObjectStorageRepository -Name "Repository 05"  Get-VBRS3CompatibleRepositorySecurityOptions -Repository $s3repository |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $s3repository variable.
2. Run the Get-VBRS3CompatibleRepositorySecurityOptions cmdlet. Set the $s3repository variable as the Repository parameter value.

Related Commands

[Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)


