---
title: "Add-VBRTapeMediaPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrtapemediapool.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Add-VBRTapeMediaPool

In this article

Short Description

Creates a new media pool.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRTapeMediaPool -Name <string> -Library <VBRTapeLibrary[]> [-Description <string>] [-Medium <VBRTapeMedium[]>] [-MoveFromFreePool] [-MoveOfflineToVault] [-Vault <VBRTapeVault>] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>] [-MediaSetCreationPolicy <VBRTapeMediaSetCreationPolicy>] [-MediaSetName <string>] [-RetentionPolicy <VBRTapeMediaPoolRetentionPolicy>] [-NextLibOffline] [-NextLibDrivesBusy] [-NextLibNoMedia] [-EnableMultiStreaming] [-SplitJobFilesBetweenDrives] [-NumberOfStreams <int>] [-WORM] [<CommonParameters>] |

Detailed Description

This cmdlet creates a new custom media pool.

Run the [Add-VBRTapeGFSMediaPool](add-vbrtapegfsmediapool.md) cmdlet to create a GFS media pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the media pool. | String | True | Named | False |
| Library | Specifies the array of tape libraries. The media pool will use tapes from these libraries.  For tape library failover, use NextLibOffline, NextLibDrivesBusy and/or NextLibNoMedia parameters to manage the failover events. Veeam will switch to the next library in order they are added to the VBRTapeLibrary object. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Description | Specifies the description for the created media pool.  If not set, Veeam Backup & Replication will enter date and time of creation by default. | String | False | Named | False |
| Medium | Specifies the array of tapes. The cmdlet will add these tapes to the media pool. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | False | Named | False |
| MoveFromFreePool | Defines that the media pool will be replenished by tapes from the Free media pool. | SwitchParameter | False | Named | False |
| MoveOfflineToVault | Defines that the tapes that go offline must be automatically moved to a vault.  Use the Vault parameter to specify the vault to which you want to move the tapes from this media pool. | SwitchParameter | False | Named | False |
| Vault | Used to set vault for the MoveOfflineToVault parameter.  Specifies the vault to which you want to automatically move the tapes. You can use one vault for several media pools. | Accepts the [VBRTapeVault](vbrtapevault.md) cmdlet, GUID or string. To get this object, run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. | False | Named | False |
| EnableEncryption | Enables encryption for the data archived to tape.  Use the EncryptionKey or KMSServer parameters to specify the encryption key you want to use to encrypt the data. | SwitchParameter | False | Named | False |
| EncryptionKey | Used to set the encryption key for the EnableEncryption parameter.  Specifies the encryption key you want to use to encrypt the data. | Accepts the [VBREncryptionKey](pscryptokey.md) object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Used to set the encryption key for the EnableEncryption parameter if you use the KMS Server for encryption.  Specifies the KMS Server you want to use to encrypt the data. | Accepts the VBRKMSServer object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| MediaSetCreationPolicy | Specifies the settings of media set you want to apply to this media pool.  If you omit this parameter, the media creation policy will be set to Never by default. | Accepts the [VBRTapeMediaSetCreationPolicy](vbrtapemediasetcreationpolicy.md) object. To create this object, run the [New-VBRTapeMediaSetCreationPolicy](new-vbrtapemediasetcreationpolicy.md) cmdlet. | False | Named | False |
| MediaSetName | Specifies the new name you want to assign to the media sets created in this media pool.  If you omit this parameter, the media set name will be set to Media set %date% by default. | String | False | Named | False |
| RetentionPolicy | Specifies the retention settings you want to apply to this media pool.  If you omit this parameter, the media set name will be set to Never by default.  Note: This parameter will not work in case you use the WORM parameter. | Accepts the [VBRTapeMediaPoolRetentionPolicy](vbrtapemediapoolretentionpolicy.md) object. To get this object, run the  cmdlet. | False | Named | False |
| NextLibOffline | Defines that the media pool will switch to the next library if the primary library is offline.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NextLibDrivesBusy | Defines that the media pool will switch to the next library if the primary library has no available drives.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NextLibNoMedia | Defines that the media pool will switch to the next library if the primary library has no available media.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableMultiStreaming | Enables the media pool to use several drives simultaneously.  Use the NumberOfStreams parameter to set the maximum number of drives that can be used.  Use the SplitJobFilesBetweenDrives parameter to indicate if the multistreaming will be used to split data between tape jobs or between source backup jobs. | SwitchParameter | False | Named | False |
| SplitJobFilesBetweenDrives | Defines that one tape job will use multiple drives to write data. Drives will process source backup jobs one by one.  Default: one drive is used for one tape job. | SwitchParameter | False | Named | False |
| NumberOfStreams | Used to set value for the EnableMultiStreaming parameter.  Specifies the maximum number of drives that the media pool can use.  Default: 2. | Int32 | False | Named | False |
| WORM | Defines that the cmdlet will add the WORM Media Pool.  Note: you cannot set retention policy when the WORM parameter is set to true.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMediaPool](vbrtapemediapool.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Media Pool with Default Settings

|  |  |
| --- | --- |
| This example shows how to create a media pool with default settings.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Add-VBRTapeMediaPool -Name "Monthly Full Backups" -MoveFromFreePool |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter values. 2. Pipe the cmdlet output to the Add-VBRTapeMediaPool cmdlet. Specify the Name parameter values. Provide the MoveFromFreePool parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Media Pool with Specific Settings

|  |  |
| --- | --- |
| This example shows how to create a media pool with the following settings:   * Offline tape are moved to vault. * Data on tape is encrypted.   |  | | --- | | $mediasetpolicy = New-VBRTapeMediaSetCreationPolicy -Type Always  $retentionpolicy = New-VBRTapeMediaPoolRetentionPolicy -Type Cyclic  $library = Get-VBRTapeLibrary -Name "Sydney\_Tape\_Server"  $media = Get-VBRTapeMedium -Name "00110001"  $vault = Get-VBRTapeVault -Name "Sydney Remote Storage"  $securepassword = Get-VBREncryptionKey -Description "Veeam Administrator"  Add-VBRTapeMediaPool -Name "AD Backups Encrypted" -Description "Active Directory Encrypted Backups" -Library $library -Medium $media -MoveOfflineToVault -Vault $vault -EnableEncryption -EncryptionKey $securepassword -MediaSetCreationPolicy $mediasetpolicy -MediaSetName "AD Daily %date%" -RetentionPolicy $retentionpolicy |  Perform the following steps:   1. Run the [New-VBRTapeMediaSetCreationPolicy](new-vbrtapemediasetcreationpolicy.md) cmdlet. Set the Always option for the Type parameter. Save the result to the $mediasetpolicy variable. 2. Run the [New-VBRTapeMediaPoolRetentionPolicy](new-vbrtapemediapoolretentionpolicy.md) cmdlet. Set the Cyclic option for the Type parameter. Save the result to the $retentionpolicy variable. 3. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save the result to the $library variable. 4. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $media variable. 5. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save the result to the $vault variable. 6. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $securepassword variable. 7. Run the Add-VBRTapeMediaPool cmdlet. Specify the following settings:  * Specify the Name and the Description parameter values. * Set the $library variable as the Library parameter value. * Set the $media variable as the Medium parameter value. * Provide the MoveOfflineToVault parameter. * Set the $vault variable as the Vault parameter value. * Provide the EnableEncryption parameter. * Set the $securepassword variable as the EncryptionKey parameter value. * Set the $mediasetpolicy variable as the MediaSetCreationPolicy parameter value. * Specify the MediaSetName parameter value. * Set the $retentionpolicy variable as the RetentionPolicy parameter value. |

Related Commands

* [Get-VBRTapeLibrary](get-vbrtapelibrary.md)
* [Get-VBRTapeMedium](get-vbrtapemedium.md)
* [Get-VBRTapeVault](get-vbrtapevault.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [New-VBRTapeMediaPoolRetentionPolicy](new-vbrtapemediapoolretentionpolicy.md)
* [New-VBRTapeMediaSetCreationPolicy](new-vbrtapemediasetcreationpolicy.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
