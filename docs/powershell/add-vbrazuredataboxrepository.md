---
title: "Add-VBRAzureDataBoxRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazuredataboxrepository.html"
last_updated: "5/15/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAzureDataBoxRepository

In this article

Short Description

Adds Azure Data Box storage as an object storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureDataBoxRepository [-Name <String>] [-Description <String>] -AzureBlobFolder <VBRAzureBlobFolder> -Connection <VBRAzureDataBoxConnection> [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <int>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds Azure Data Box storage as an object storage repository to the backup infrastructure.

|  |
| --- |
| Important |
| This cmdlet adds the Azure Data Box storage that can be used as a capacity extent of the scale-out backup repository. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AzureBlobFolder | Specifies an Azure Data Box folder. The cmdlet will move the backup files to the specified folder. | Accepts the VBRAzureBlobFolder object. To get this object, run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with Azure Data Box storage that you want to add as the backup repository. | Accepts the VBRAzureDataBoxConnection object. To create this object, run the [Connect-VBRAzureDataBoxService](connect-vbrazuredataboxservice.md) cmdlet. | True | Named | False |
| Name | Specifies a name of Azure Data Box storage. The cmdlet will add Azure Data Box storage to Veeam Backup & Replication with this name. | String | False | Named | False |
| Description | Specifies a description of Azure Data Box storage. The cmdlet will add Azure Data Box storage to Veeam Backup & Replication with this description. | String | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks parameter to specify the number of tasks. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureDataBoxRepository](vbrazuredataboxrepository.md)

Example

Adding Azure Data Box Storage to Backup Infrastructure

This example shows how to add the DataBox 009 Azure Data Box storage to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureDataBoxService -Account $account -ServicePoint "http://123.45.67.89:9000"  $container = Get-VBRAzureBlobContainer -Connection $connect  $folder = Get-VBRAzureBlobFolder -Container $container -Connection $connect  Add-VBRAzureDataBoxRepository -AzureBlobFolder $folder -Connection $connect -Name "DataBox 009" |

Perform the following steps;

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRAzureDataBoxService](connect-vbrazuredataboxservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the ServicePoint parameter value. Save the result to the $connect variable.
3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Set the $connect variable as the Connection parameter value. Save the result to the $container variable.
4. Run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. Set the $container variable as the Container parameter value. Set the $connect variable as the Connection parameter value. Save the result to the $folder variable.
5. Run the Add-VBRAzureDataBoxRepository cmdlet. Specify the following settings:

* Set the $folder variable as the AzureBlobFolder parameter value.
* Set the $connect variable as the Connection parameter value.
* Specify the Name parameter value.

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureDataBoxService](connect-vbrazuredataboxservice.md)
* [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md)
* [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md)

Page updated 5/15/2024

Page content applies to build 13.0.1.1071
