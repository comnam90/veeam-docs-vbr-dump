---
title: "Add-VBRAzureBlobAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazureblobaccount.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAzureBlobAccount


Short Description

Creates Microsoft Azure Blob credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureBlobAccount -Name <string> -SharedKey <string> [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VBRAzureBlobAccount object. This object contains credentials records of a Microsoft Azure storage account that has permissions to access the Blob storage resources.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a login name. The cmdlet will use this login name to add the Microsoft Azure Blob credentials record. | String | True | Named | False |
| SharedKey | Specifies a shared key. The cmdlet will use this shared key to add the Microsoft Azure Blob credentials record. | String | True | Named | False |
| Description | Specifies a description for the Microsoft Azure Blob credentials record. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureBlobAccount object that contains Microsoft Azure Blob credentials records.

Examples

Adding Microsoft Azure Blob Credentials Record

This example shows how to add an Microsoft Azure Blob credentials record.

|  |
| --- |
| $securepassword = Read-Host "Enter your password" -AsSecureString  Enter your password: \*\*\*\*\*\*\*\*\*\*  Add-VBRAzureBlobAccount -Name "Login" -SharedKey $securepassword |

Perform the following steps:

1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6) cmdlet. Specify the message that the console will display as a prompt. Provide the AsSecureString parameter. Save the result to the $securepassword variable.
2. Enter the password.
3. Run the Add-VBRAzureBlobAccount cmdlet. Specify the Name parameter value. Set the $securepassword variable as the SharedKey parameter value.


