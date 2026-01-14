---
title: "Set-VBRTapeMediaPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapemediapool.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRTapeMediaPool

In this article

Short Description

Modifies a media pool.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeMediaPool -MediaPool <VBRTapeMediaPool> -Library <VBRTapeLibrary[]> [-Name <string>] [-Description <string>] [-MoveFromFreePool] [-MoveOfflineToVault] [-Vault <VBRTapeVault>] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>] [-MediaSetCreationPolicy <VBRTapeMediaSetCreationPolicy>] [-MediaSetName <string>] [-RetentionPolicy <VBRTapeMediaPoolRetentionPolicy>] [-Medium <VBRTapeMedium[]>] [-NextLibOffline] [-NextLibDrivesBusy] [-NextLibNoMedia] [-EnableMultiStreaming] [-NumberOfStreams <int>] [-SplitJobFilesBetweenDrives] [-PassThru] [-Mode <string> {Paralleling | Failover}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the media pool that was created before.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| MediaPool | Specifies the media pool you want to modify. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Library | Specifies the array of tape libraries whose tapes will be used in this media pool.  Use the NextLibOffline, NextLibDrivesBusy and/or NextLibNoMedia parameters to manage the libraries. Veeam Backup & Replication will switch to the next library in order they are added to the [VBRTapeLibrary](vbrtapelibrary.md) object. | Accepts the [VBRTapeLibrary[]](vbrtapelibrary.md) object, GUID or string type. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByProperty Name) |
| Name | Specifies the new name you want to assign to the media pool. | String | False | Named | False |
| Description | Specifies the description for the media pool. | String | False | Named | False |
| Medium | Specifies the array of tapes you want to add to the media pool. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | False | Named | False |
| MoveFromFreePool | Defines if new tapes will be allocated from the Free media pool when needed.  If you provide this parameter, the media pool will be replenished by tapes from the Free media pool. | SwitchParameter | False | Named | False |
| MoveOfflineToVault | Defines that the tapes that go offline must be automatically moved to a vault.  Use the Vault parameter to specify the vault to which you want to move the tapes from this media pool. | SwitchParameter | False | Named | False |
| Vault | Used to set vault for the MoveOfflineToVault parameter.  Specifies the vault to which you want to automatically move the tapes. You can use one vault for several media pools. | Accepts the [VBRTapeVault](vbrtapevault.md) object, GUID or string type. To get this object, run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. | False | Named | False |
| EnableEncryption | Enables data encryption for data archived to tape.  Use the EncryptionKey or KMSServer parameter to specify the encryption key you want to use to encrypt the data. | SwitchParameter | False | Named | False |
| EncryptionKey | Used to set the encryption key for the EnableEncryption parameter.  Specifies the encryption key you want to use to encrypt the data. | Accepts the [VBREncryptionKey](pscryptokey.md) object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Used to set the encryption key for the EnableEncryption parameter if you use the KMS Server for encryption.  Specifies the KMS Server you want to use to encrypt the data. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| MediaSetCreationPolicy | Specifies the settings of media set you want to apply to this media pool.  If omitted, the media creation policy will be set to Never by default. | Accepts the [VBRTapeMediaSetCreationPolicy](vbrtapemediasetcreationpolicy.md) object. To create this object, run the [New-VBRTapeMediaSetCreationPolicy](new-vbrtapemediasetcreationpolicy.md) cmdlet. | False | Named | False |
| MediaSetName | Specifies the new name you want to assign to the media sets created in this media pool.  If omitted, the media set name will be set to Media set %date% by default. | String | False | Named | False |
| RetentionPolicy | Specifies the retention settings you want to apply to this media pool.  If omitted, the media set name will be set to Never by default. | Accepts the [VBRTapeMediaPoolRetentionPolicy](vbrtapemediapoolretentionpolicy.md) object. To create this object, run the [New-VBRTapeMediaPoolRetentionPolicy](new-vbrtapemediapoolretentionpolicy.md) cmdlet. | False | Named | False |
| NextLibOffline | Defines that the media pool will switch to the next library if the primary library is offline.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NextLibDrivesBusy | Defines that the media pool will switch to the next library if the primary library has no available drives.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NextLibNoMedia | Defines that the media pool will switch to the next library if the primary library has no available media.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableMultiStreaming | Defines that the media pool can use several drives simultaneously.  Use the NumberOfStreams parameter to set the maximum number of drives that can be used. | SwitchParameter | False | Named | False |
| SplitJobFilesBetweenDrives | Defines that the backup files within one backup set will be written with several drives to several tapes.  Otherwise, one tape job will use one drive. | SwitchParameter | False | Named | False |
| NumberOfStreams | Used to set value for the EnableMultiStreaming parameter.  Defines the maximum number of drives that the media pool can use.  Default: 2. | Int32 | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| Mode | Specifies the tape media pool mode.  You can set either of the following modes:   * Paralleling: if you set this mode, the tape job will use drives in all libraries in parallel. * Failover: if you set this mode, the tape job will use the first library in the list to write data. Other libraries from this media pool will be passive and will be used for failover. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMediaPool](vbrtapemediapool.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Media Pool to Move Offline Tapes to Vault

|  |  |
| --- | --- |
| This example shows how to instruct a selected media pool to move the offline tapes to a tape vault.  |  | | --- | | $mediapool = Get-VBRTapeMediaPool -Name "File Backup Media Pool"  $library = Get-VBRTapeLibrary -Name "Sydney\_Tape\_Server"  $vault = Get-VBRTapeVault -Name "Sydney Remote Storage"  Set-VBRTapeMediaPool -MediaPool $mediapool -Library $library -MoveOfflineToVault -Vault $vault |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $mediapool variable. 2. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save it to the $library variable. 3. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save it to the $vault variable. 4. Run the Set-VBRTapeMediaPool cmdlet. Specify the following settings:  * Set the $mediapool variable as the MediaPool parameter value. * Set the $library variable as the Library parameter value. * Provide the MoveOfflineToVault parameter. * Set the $vault variable as the Vault parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Encryption Settings to Media Pool

|  |  |
| --- | --- |
| This example shows how to add encryption settings to a selected media pool.  |  | | --- | | $mediapool = Get-VBRTapeMediaPool -Name "File Backup Media Pool"  $library = Get-VBRTapeLibrary -Name "Sydney\_Tape\_Server"  $encryptionkey = Get-VBREncryptionKey -Description "Veeam Administrator"  Set-VBRTapeMediaPool -MediaPool $mediapool -Library $library -EnableEncryption -EncryptionKey $encryptionkey |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $mediapool variable. 2. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save it to the $library variable. 3. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save it to the $encryptionkey variable. 4. Run the Set-VBRTapeMediaPool cmdlet. Specify the following settings:  * Set the $mediapool variable as the MediaPool parameter value. * Set the $library variable as the Library parameter value. * Provide the EnableEncryption parameter. * Set the $encryptionkey variable as the EncryptionKey parameter value. |

Related Commands

* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [Get-VBRTapeLibrary](get-vbrtapelibrary.md)
* [Get-VBRTapeMedium](get-vbrtapemedium.md)
* [Get-VBRTapeVault](get-vbrtapevault.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [New-VBRTapeMediaPoolRetentionPolicy](new-vbrtapemediapoolretentionpolicy.md)
* [New-VBRTapeMediaSetCreationPolicy](new-vbrtapemediasetcreationpolicy.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
