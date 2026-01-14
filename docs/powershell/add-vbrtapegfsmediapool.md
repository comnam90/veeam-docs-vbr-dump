---
title: "Add-VBRTapeGFSMediaPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrtapegfsmediapool.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Add-VBRTapeGFSMediaPool

In this article

Short Description

Creates a new GFS media pool.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRTapeGFSMediaPool -Name <string> -Library <VBRTapeLibrary[]> [-Description <string>] [-Medium <VBRTapeMedium[]>] [-MoveFromFreePool] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>] [-NextLibOffline] [-NextLibDrivesBusy] [-NextLibNoMedia] [-DailyOverwritePeriod <int>] [-WeeklyOverwritePeriod <int>] [-MonthlyOverwritePeriod <int>] [-QuarterlyOverwritePeriod <int>] [-YearlyOverwritePeriod <int>] [-DailyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-WeeklyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-MonthlyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-QuarterlyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-YearlyMediaSetPolicy <VBRTapeGFSMediaSetPolicy>] [-EnableMultiStreaming] [-SplitJobFilesBetweenDrives] [-NumberOfStreams <int>] [-WORM]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new GFS media pool. The media sets are created with default settings.

Run the [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md) cmdlet to set other options for media sets.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the media pool. | String | True | Named | False |
| Library | Specifies the array of tape libraries. The media pool will use tapes from these libraries.  For tape library failover, use NextLibOffline, NextLibDrivesBusy and/or NextLibNoMedia parameters to manage the failover events. Veeam will switch to the next library in order they are added to the VBRTapeLibrary object. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Medium | Specifies the array of tapes. The cmdlet will add these tapes to the media pool. | Accepts the [VBRTapeMedium](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | False | Named | False |
| Description | Specifies the description for the created media pool.  If not set, Veeam will enter date and time of creation by default. | String | False | Named | False |
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
| SplitJobFilesBetweenDrives | Defines that one tape job will use multiple drives to write data. Drives will process source backup jobs one by one.  Default: one drive is used for one tape job. | SwitchParameter | False | Named | False |
| NumberOfStreams | Used to set value for the EnableMultiStreaming parameter.  Indicates the maximum number of drives that the media pool can use.  Default: 2. | Int32 | False | Named | False |
| WORM | Defines that the cmdlet will add the WORM Media Pool.  Note: you cannot set retention policy when the WORM parameter is set to true.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeGFSMediaPool](vbrtapegfsmediapool.md)

Examples

Creating GFS Media Pool with Default Settings and Custom Retention Periods

This example shows how to create a GFS media pool with default settings and customized retention periods.

|  |
| --- |
| $library = Get-VBRTapeLibrary -Name "HP MSL G3 Series 9.50"  $encryption = Get-VBREncryptionKey -Description "Veeam Administrator"  Add-VBRTapeGFSMediaPool -Name "GFS Media Pool" -Library $library -MoveFromFreePool -EnableEncryption -EncryptionKey $encryption -DailyOverwritePeriod 30 -WeeklyOverwritePeriod 8 -MonthlyOverwritePeriod 12 -QuarterlyOverwritePeriod 8 -YearlyOverwritePeriod 5 |

Perform the following steps:

1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save the result to the $library variable.
2. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result it to the $encryption variable.
3. Run the Add-VBRTapeGFSMediaPool cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $library variable as the Library parameter value.
* Provide the MoveFromFreePool parameter.
* Provide the EnableEncryption parameter.
* Set the $encryption variable as the EncryptionKey parameter value.
* To define retention settings, provide the DailyOverwritePeriod, WeeklyOverwritePeriod, MonthlyOverwritePeriod, QuarterlyOverwritePeriod, YearlyOverwritePeriod parameter values.

Related Commands

* [Get-VBRTapeLibrary](get-vbrtapelibrary.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [New-VBRTapeGFSMediaSetPolicy](new-vbrtapegfsmediasetpolicy.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
