---
title: "Set-VBRTapeGFSMediaPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapegfsmediapool.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRTapeGFSMediaPool

In this article

Short Description

Modifies a GFS media pool.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeGFSMediaPool -MediaPool <VBRTapeGFSMediaPool> [-Name <string>] [-Description <string>] [-Library <VBRTapeLibrary[]>] [-Medium <VBRTapeMedium[]>] [-MoveFromFreePool] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>] [-NextLibOffline] [-NextLibDrivesBusy] [-NextLibNoMedia] [-DailyOverwritePeriod <int>] [-WeeklyOverwritePeriod <int>] [-MonthlyOverwritePeriod <int>] [-QuarterlyOverwritePeriod <int>] [-YearlyOverwritePeriod <int>] [-DailyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-WeeklyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-MonthlyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-QuarterlyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-YearlyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-EnableMultiStreaming] [-NumberOfStreams <int>] [-SplitJobFilesBetweenDrives] [-PassThru] [-Mode <string> {Paralleling | Failover}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a GFS media pool.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| MediaPool | Specifies the GFS media pool you want to modify. | Accepts the [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the media pool. | String | True | Named | False |
| Library | Specifies the array of tape libraries. The media pool will use tapes from these libraries.  For tape library failover, use NextLibOffline, NextLibDrivesBusy and/or NextLibNoMedia parameters to manage the failover events. Veeam will switch to the next library in order they are added to the VBRTapeLibrary object. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByProperty Name) |
| Description | Specifies the description for the created media pool.  If not set, Veeam will enter date and time of creation by default. | String | False | Named | False |
| Medium | Specifies the array of tapes. The cmdlet will add these tapes to the media pool. | Accepts the [VBRTapeMedium](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | False | Named | False |
| MoveFromFreePool | Defines that the media pool will be replenished by tapes from the Free media pool. | SwitchParameter | False | Named | False |
| EnableEncryption | Enables data encryption for data archived to tape.  Use the EncryptionKey or KMSServer parameter to specify the encryption key you want to use to encrypt the data. | SwitchParameter | False | Named | False |
| EncryptionKey | Used to set the encryption key for the EnableEncryption parameter.  Specifies the encryption key you want to use to encrypt the data. | Accepts the [VBREncryptionKey](pscryptokey.md) object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Used to set the encryption key for the EnableEncryption parameter if you use the KMS Server for encryption.  Specifies the KMS Server you want to use to encrypt the data. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| NextLibOffline | Defines that the media pool will switch to the next library if the primary library is offline.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NextLibDrivesBusy | Defines that the media pool will switch to the next library if the primary library has no available drives.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NextLibNoMedia | Defines that the media pool will switch to the next library if the primary library has no available media.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| DailyOverwritePeriod | Indicates the data retention period for the daily media set (days). | Int32 | False | Named | False |
| WeeklyOverwritePeriod | Indicates the data retention period for the weekly media set (weeks). | Int32 | False | Named | False |
| MonthlyOverwritePeriod | Indicates the data retention period for the monthly media set (months). | Int32 | False | Named | False |
| QuarterlyOverwritePeriod | Indicates the data retention period for the quarterly media set (months). | Int32 | False | Named | False |
| YearlyOverwritePeriod | Indicates the data retention period for the yearly media set (years). | Int32 | False | Named | False |
| DailyMediaSetPolicy | Specifies settings for the daily media set. | Accepts the [VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md) object. To create this object, run the [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md) cmdlet. | False | Named | False |
| WeeklyMediaSetPolicy | Specifies settings for the weekly media set. | Accepts the [VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md) object. To create this object, run the [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md) cmdlet. | False | Named | False |
| MonthlyMediaSetPolicy | Specifies settings for the monthly media set. | Accepts the [VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md) object. To create this object, run the [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md) cmdlet. | False | Named | False |
| QuarterlyMediaSetPolicy | Specifies settings for the quarterly media set. | Accepts the [VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md) object. To create this object, run the [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md) cmdlet. | False | Named | False |
| YearlyMediaSetPolicy | Specifies settings for the yearly media set. | Accepts the [VBRTapeGFSMediaSetPolicy](vbrtapegfsmediasetpolicy.md) object. To create this object, run the [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md) cmdlet. | False | Named | False |
| EnableMultiStreaming | Enables the media pool to use several drives simultaneously.  Use the NumberOfStreams parameter to set the maximum number of drives that can be used.  Use the SplitJobFilesBetweenDrives parameter to indicate if the multistreaming will be used to split data between tape jobs or between source backup jobs. | SwitchParameter | False | Named | False |
| NumberOfStreams | Used to set value for the EnableMultiStreaming parameter.  Indicates the maximum number of drives that the media pool can use.  Default: 2. | Int32 | False | Named | False |
| SplitJobFilesBetweenDrives | Defines that one tape job will use multiple drives to write data. Drives will process source backup jobs one by one.  Default: one drive is used for one tape job. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| Mode | Specifies the tape media pool mode.  You can set either of the following modes:   * Paralleling: if you set this mode, the tape job will use drives in all libraries in parallel. * Failover: if you set this mode, the tape job will use the first library in the list to write data. Other libraries from this media pool will be passive and will be used for failover. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeGFSMediaPool](vbrtapegfsmediapool.md)

Examples

Enabling Media Pool to Use Multiple Drives Simultaneously

This example instructs a selected media pool to use up to 4 drives simultaneously.

|  |
| --- |
| $mpool = Get-VBRTapeMediaPool -Name "GFS Media Pool"  Set-VBRTapeGFSMediaPool -MediaPool $mpool -EnableMultiStreaming -NumberOfStreams 4 |

Perform the following steps:

1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $mpool variable.
2. Run the Set-VBRTapeGFSMediaPool cmdlet. Set the $mpool variable as the MediaPool parameter value. Provide the EnableMultiStreaming parameter. Specify the NumberOfStreams parameter value.

Related Commands

* [Get-VBRTapeLibrary](get-vbrtapelibrary.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
