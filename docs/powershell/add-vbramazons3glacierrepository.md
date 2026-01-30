---
title: "Add-VBRAmazonS3GlacierRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbramazons3glacierrepository.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAmazonS3GlacierRepository


Short Description

Adds Amazon S3 Glacier archive storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAmazonS3GlacierRepository -Connection <VBRAmazonS3Connection> -AmazonS3Folder <VBRAmazonS3Folder> [-AmazonProxySpec <VBRAmazonEC2ProxyAppliance>] [-Name <String>] [-Description <String>] [-UseDeepArchive] [-UseInstantRetrieval] [-EnableBackupImmutability] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds Amazon S3 Glacier archive storage repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with an Amazon S3 Glacier object storage that you want to add as an archive repository. | Accepts the VBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet and set the ArchiveTier property as the ServiceType parameter value. | True | Named | False |
| AmazonS3Folder | Specifies an Amazon S3 folder. Veeam Backup & Replication will move backup files into this folder. | Accepts the VBRAmazonS3Folder object. To create this object, run the [New-VBRAmazonS3Folder](new-vbramazons3folder.md) cmdlet. | True | Named | True (ByValue) |
| AmazonProxySpec | Specifies the archiver appliance that will transfer the data from Amazon S3 to Amazon S3 Glacier object storage. | Accepts the VBRAmazonEC2ProxyAppliance object. To create this object, run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. | False | Named | True (ByPropertyName) |
| Name | Specifies a name of an Amazon S3 Glacier object storage. The cmdlet will add object storage with this name. | String | False | Named | False |
| Description | Specifies a description of an Amazon S3 Glacier object storage. The cmdlet will add object storage with this description. | String | False | Named | False |
| UseDeepArchive | Defines that the cmdlet will create a repository where blocks are marked with the Glacier Deep Archive storage class.  Note: If you do not provide the UseDeepArchive and UseInstantRetrieval parameters, the cmdlet will create a repository where blocks are marked as the Amazon S3 Glacier Flexible Retrieval storage class.    Default: False. | SwitchParameter | False | Named | False |
| UseInstantRetrieval | Defines that the cmdlet will create a repository where blocks are marked with the Amazon S3 Glacier Instant Retrieval storage class.  Note: If you do not provide the UseDeepArchive and UseInstantRetrieval parameters, the cmdlet will create a repository where blocks are marked as the Amazon S3 Glacier Flexible Retrieval storage class.    Default: False. | SwitchParameter | False | Named | False |
| EnableBackupImmutability | Enables the immutability option.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonS3GlacierRepository](vbramazons3glacierrepository.md)

Examples

Adding Amazon S3 Glacier Repository to Backup Infrastructure

This example shows how to add Amazon S3 Glacier object storage as a backup repository to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRAmazonAccount -AccessKey "XXXXXXXXXXXXXXXXXXX" -SecretKey "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"  $bucket = Get-VBRAmazonS3Bucket -Connection $connection -Name "connect"  $folder = Get-VBRAmazonS3Folder -Connection $connection -Bucket $bucket -Name "veeam"  $region = Get-VBRAmazonS3Region -Account $account -RegionType Global -Name "ap-northeast-1"  $instance = Get-VBRAmazonEC2InstanceType -Region $region -Name "al.xlarge"  $vpc = Get-VBRAmazonEC2VPC -Region $region  $sgroup = Get-VBRAmazonEC2SecurityGroup -VPC $vpc -Name "veeamvpc"  $subnet = Get-VBRAmazonEC2Subnet -VPC $vpc -Name "veeamsubnet"  $proxy = New-VBRAmazonEC2ProxyAppliance -InstanceType $instance -Subnet $subnet -SecurityGroup $sgroup -RedirectorPort 443  Add-VBRAmazonS3GlacierRepository -Connection $connection -AmazonS3Folder $folder -AmazonProxySpec $proxy -Name Repository09 |

Perform the following steps:

1. Specify Amazon connection settings:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey and SecretKey parameter values. Save the result to the $account variable.

1. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable.

1. Specify object storage settings:

1. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connection variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $bucket variable.
2. Run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. Set the $connection variable as the Connection parameter value. Set the $bucket variable as the Bucket parameter value. Specify the Name parameter value. Save the result to the $folder variable.

1. Define the Amazon proxy settings:

1. Run the [Get-VBRAmazonS3Region](get-vbramazons3region.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and Name parameter values. Save the result to the $region variable.
2. Run the [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md) cmdlet. Set the $region variable as the Region parameter value. Specify the Name parameter value. Save the result to the $instance variable.
3. Run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $vpc variable.
4. Run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. Set the $vpc variable as the VPC parameter value. Specify the Name parameter value. Save the result to the $sgroup variable.
5. Run the [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md) cmdlet. Set the $vpc variable as the VPC parameter value. Specify the Name parameter value. Save the result to $subnet variable.
6. Run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. Set the $instance variable as the InstanceType parameter value. Set the $subnet variable as the Subnet parameter value. Set the $sgroup variable as the SecurityGroup parameter value. Specify the RedirectorPort parameter value. Save the result to $proxy variable.

1. Run the Add-VBRAmazonS3GlacierRepository cmdlet. Specify the following settings:

* Set the $connection variable as the Connection parameter value.
* Set the $folder variable as the Folder parameter value.
* Set the $proxy variable as the Proxy parameter value.
* Specify the Name parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)
* [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md)
* [Get-VBRAmazonS3Folder](get-vbramazons3folder.md)
* [Get-VBRAmazonS3Region](get-vbramazons3region.md)
* [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md)
* [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md)
* [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md)
* [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md)
* [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md)


