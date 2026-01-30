---
title: "Send-VBRScaleOutBackupRepositoryReport"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/send-vbrscaleoutbackuprepositoryreport.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Send-VBRScaleOutBackupRepositoryReport


Short Description

Sends reports on processing results of scale-out backup repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Send-VBRScaleOutBackupRepositoryReport -Repository <VBRScaleOutBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet sends reports that contain information on processing results of scale-out backup repositories. For more information on reports for scale-out backup repositories, see the [Receiving Scale-Out Backup Repository Reports](https://helpcenter.veeam.com/docs/vbr/userguide/sobr_reports.html?ver=13) section of User Guide for VMware vSphere.

|  |
| --- |
| ![Send-VBRScaleOutBackupRepositoryReport](images/icon_important.webp) Important! |
| Before running this cmdlet, you must configure global email notification settings. For more information on setting global email notification settings, see the [Configuring Global Email Notification Settings](https://helpcenter.veeam.com/docs/vbr/userguide/general_email_notifications.html?ver=13) section of the User Guide for VMware vSphere. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a scale-out backup repository. The cmdlet will send a report on processing results of this scale-out backup repository. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet and provide the ScaleOut parameter. | True | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Sending Report on Scale-Out Repository Processing Results

This example shows how to send a report on processing results of a scale-out backup repository.

|  |
| --- |
| $scaleoutrepository = Get-VBRBackupRepository -ScaleOut -Name "Amazon S3"  Send-VBRScaleOutBackupRepositoryReport -Repository $scaleoutrepository |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Specify the Name parameter value. Save the result to the $scaleoutrepository variable.
2. Run the Send-VBRScaleOutBackupRepositoryReport cmdlet. Set the $scaleoutrepository variable as the Repository parameter value.

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)


