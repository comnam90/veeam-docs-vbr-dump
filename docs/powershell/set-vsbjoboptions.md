---
title: "Set-VSBJobOptions (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vsbjoboptions.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Set-VSBJobOptions (obsolete)


Short Description

Applies custom SureBackup job options.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VSBJobOptions -Job <CSbJob> -Options <CDRJobOptions> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies customized job options to SureBackup jobs.

To customize the SureBackup job options you need to first run the [New-VSBJobOptions](new-vsbjoboptions.md) cmdlet. The [New-VSBJobOptions](new-vsbjoboptions.md) cmdlet returns the CDRJobOptions object containing the set of default SureBackup job options. You can customize any of these options and apply further to a SureBackup job.

Run the [Set-VBRJobOptions](set-vbrjoboptions.md) cmdlet to edit job options of backup, replication or copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of SureBackup jobs. The cmdlet will apply the selected options to these jobs. | Accepts the CSbJob object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Options | Specifies the SureBackup job options you want to apply. | Accepts the CDRJobOptions object. To get this object, run the [New-VSBJobOptions](new-vsbjoboptions.md) cmdlet. | True | 2 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Scheduling SureBackup Jobs to Run Daily

|  |  |
| --- | --- |
| This example shows how to apply the customized options to the SureBackup Job 01 SureBackup job.  |  | | --- | | $SureOptions = New-VSBJobOptions  $SureOptions.EmailNotification = $true  $SureOptions.EmailNotificationAddresses = "mailto@veeam.com"  Get-VBRJob -Name "SureBackup Job 01" | Set-VSBJobOptions -Options $SureOptions |  Perform the following steps:   1. Run the New-VSBJobOptions cmdlet. Save the result to the $SureOptions variable. 2. Provide the $true value for the EmailNotification property of the $SureOptions variable. 3. Specify the value for the EmailNotificationAddresses property. 4. Run the Get-VSBJob cmdlet. Specify the Name parameter value. 5. Pipe the cmdlet output to the Set-VSBJobOptions cmdlet. Set the $SureOptions variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Scheduling SureBackup Jobs to Run Daily

|  |  |
| --- | --- |
| This example shows how to apply the customized options to the SureBackup Job 01 SureBackup job.  |  | | --- | | $SureOptions = New-VSBJobOptions  $SureOptions.EmailNotification = $true  $SureOptions.EmailNotificationAddresses = "mailto@veeam.com"  $SureJob = Get-VSBJob -Name "SureBackup Job 01"  Set-VSBJobOptions -Job $SureJob -Options $SureOptions |  Perform the following steps:   1. Run the New-VSBJobOptions cmdlet. Save the result to the $SureOptions variable. 2. Provide the $true value for the EmailNotification property of the $SureOptions variable. 3. Specify the value for the EmailNotificationAddresses property. 4. Run the Get-VSBJob cmdlet. Specify the Name parameter value. Save the result to the $SureJob variable. 5. Run the Set-VSBJobOptions cmdlet. Set the $SureJob variable as the Job parameter value. Set the $SureOptions variable as the Options parameter value. |

Related Commands

[Get-VSBJob](get-vsbjob.md)


