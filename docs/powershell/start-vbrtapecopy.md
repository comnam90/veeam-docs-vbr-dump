---
title: "Start-VBRTapeCopy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtapecopy.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Start-VBRTapeCopy

In this article

Short Description

Starts tape copy jobs.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRTapeCopy -TapeMedium <VBRTapeMedium[]> -TargetMediaPool <VBRTapeMediaPoolBase> [-Wait] [-DependentTapeMedium <VBRTapeMedium[]>] [-EnableHardwareCompression] [-SkipDependencyCheck] [-SkipEncryptedBackups] [-AddDependentMediumAutomatically] [-PreserveOriginalRetention] [-ExportSourceTape] [-ExportTargetTape] [-TargetLibrary <VBRTapeLibrary>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts tape copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| TapeMedium | Specifies an array of tapes. The cmdlet will add this array of tapes to the tape copy job. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | False |
| TargetMediaPool | Specifies a media pool. The cmdlet will copy the tape data to this media pool.  Note: If the target media pool contains several tape libraries, the TargetLibrary parameter is required. | Accepts the [VBRTapeMediaPoolBase](vbrtapemediapoolbase.md) object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |
| DependentTapeMedium | Specifies an array of dependent tapes. The cmdlet will add this array of dependent tapes to the tape copy job.  When a backup file does not fit on one tape, it is divided into parts and written to several tapes. These tapes are considered dependent.  Note: If you do not specify the DependentTapeMedium and SkipDependencyCheck parameters, but dependent media exist, you will get the warning about that with the prompt to add these media to the tape copy job. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeCopyDependentMedium](get-vbrtapecopydependentmedium.md) cmdlet. | False | Named | False |
| EnableHardwareCompression | Enables the hardware compression option. If set to False, the the hardware compression option is disabled.  If you do not provide this parameter, the hardware compression option is still enabled. | SwitchParameter | False | Named | False |
| SkipDependencyCheck | Defines that the existence of dependent tapes is not checked.  Note: If you do not specify the DependentTapeMedium and SkipDependencyCheck parameters, but dependent media exist, you will get the warning about that with the prompt to add these media to the tape copy job. | SwitchParameter | False | Named | False |
| SkipEncryptedBackups | Defines that the cmdlet will skip encrypted backups stored on the source tape from the tape copy job.  If you do not provide this parameter and there are encrypted backups on tapes to copy, the cmdlet cannot copy these encrypted backups and will return a warning. | SwitchParameter | False | Named | False |
| AddDependentMediumAutomatically | Defines that the cmdlet will add dependent tapes to the tape copy job automatically.  If you do not provide this parameter and there are dependent tapes, the cmdlet cannot copy files written to dependent tapes and will return a warning. | SwitchParameter | False | Named | False |
| PreserveOriginalRetention | Defines that retention settings of the source media pool are copied to the target media pool. If set to False, the target media pool will use its own retention settings.  If you do not provide this parameter, retention settings are still copied from the source media pool to the target media pool. | SwitchParameter | False | Named | False |
| ExportSourceTape | Defines that the source tapes will be exported after the tape copy job finishes.  If you do not provide this parameter, the source tapes will not be exported after the tape copy job finishes. | SwitchParameter | False | Named | False |
| ExportTargetTape | Defines that the target tapes will be exported after the tape copy job finishes.  If you do not provide this parameter, the target tapes will not be exported after the tape copy job finishes. | SwitchParameter | False | Named | False |
| TargetLibrary | Specifies a tape library. The cmdlet will copy the tape data to this tape library.  Note: This parameter is required if the target media pool contains several tape libraries. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Tape Copy Job

This example shows how to start a tape copy job with the following settings:

* The copy job will process data that is stored on the 0021000C tape and all dependent tapes.
* The copy job will copy data to the Copy media pool.
* The copy job will apply retention settings of the original medial pool to the target media pool.
* The copy job will run with the enabled hardware compression option.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "0021000C"  $pool = Get-VBRTapeMediaPool -Name "Copy"  Start-VBRTapeCopy -TapeMedium $tape -TargetMediaPool $pool -Wait -EnableHardwareCompression -AddDependentMediumAutomatically -PreserveOriginalRetention |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $pool variable.
3. Run the Start-VBRTapeCopy cmdlet. Specify the following settings:

* Set the $tape variable as the TapeMedium parameter value.
* Set the $pool variable as the TargetMediaPool parameter value.
* Provide the Wait parameter.
* Provide the EnableHardwareCompression parameter.
* Provide the AddDependentMediumAutomatically parameter.
* Provide the PreserveOriginalRetention parameter.

Related Commands

* [Get-VBRTapeMedium](get-vbrtapemedium.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
