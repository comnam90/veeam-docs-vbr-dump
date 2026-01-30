---
title: "Start-VBRTapeRestoreAllContent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtaperestoreallcontent.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Start-VBRTapeRestoreAllContent


Short Description

Starts restoring all content of the specified tapes.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRTapeRestoreAllContent -TapeMedium <VBRTapeMedium[]> -Server <CHost> -Path <string> [-DependentTapeMedium <VBRTapeMedium[]>] [-SkipDependencyCheck] [-AddDependentMediumAutomatically] [-Security] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restoring all content of the specified tapes.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| TapeMedium | Specifies an array of tapes. The cmdlet will add this array of tapes to the tape restore job. | Accepts the [VBRTapeMedium](vbrtapemedium.md)[]object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | False |
| Server | Specifies the target server. The cmdlet will restore the content of the tapes to this server. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the folder. The cmdlet will restore the content of the tapes to this folder. | String | True | Named | False |
| DependentTapeMedium | Specifies an array of dependent tapes. The cmdlet will add this array of dependent tapes to the entire tape restore job.  When a backup file does not fit on one tape, it is divided into parts and written to several tapes. These tapes are considered dependent.  Note: If you do not specify the DependentTapeMedium and SkipDependencyCheck parameters, but dependent media exist, you will get a warning. If you want to restore all content of the the tapes included into the tape restore job including file parts stored on dependent tapes, confirm addition of the missing dependent tapes to the job. If dependent tapes are unavailable, for example, they are physically destroyed, you can try to restore data stored only on the specified tapes. In this case, do not confirm addition of dependent tapes to the job. | Accepts the [VBRTapeMedium](vbrtapemedium.md)object. To get this object, run the [Get-VBRTapeCopyDependentMedium](get-vbrtapecopydependentmedium.md) cmdlet. | False | Named | False |
| SkipDependencyCheck | Defines that the existence of dependent tapes is not checked.  Note: If you do not specify the DependentTapeMedium and SkipDependencyCheck parameters, but dependent media exist, you will get a warning. If you want to restore all content of the the tapes included into the tape restore job including file parts stored on dependent tapes, confirm addition of the missing dependent tapes to the job. If dependent tapes are unavailable, for example, they are physically destroyed, you can try to restore data stored only on the specified tapes. In this case, do not confirm addition of dependent tapes to the job. | SwitchParameter | False | Named | False |
| AddDependentMediumAutomatically | Defines that the cmdlet will automatically add tapes that are dependent on the media added to tape restore job.  If you do not provide this parameter and you have dependent tapes, the cmdlet will not be able to copy files written to dependent tapes and will return a warning. | SwitchParameter | False | Named | False |
| Security | Defines that the files will be restored with the original security settings. Otherwise the file/folder security settings will be inherited from the parent item. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CRestoreSession object that contains the following details on the started tape restore session: Restore Type, State, Start Time, End Time, Description.

Examples

Restoring All Tape Content

This example shows how to start a tape job for restoring all content of the tape with the following settings:

* The tape restore job will process data that is stored on the 0021000C tape and all dependent tapes. Dependent tapes will be found and added to the job automatically.
* The tape restore job will restore the entire tape content to qa10.tech.local server and will store it at C:\Restored Backup\Tapes path.
* The tape restore job will apply security settings of the original content to the restored content.
* The copy job will run with the enabled hardware compression option.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "0021000C"  Start-VBRTapeRestoreAllContent -TapeMedium $tape -Server "qa10.tech.local" -Path "C:\Restored Backup\Tapes" -AddDependentMediumAutomatically -Security |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Start-VBRTapeRestoreAllContent cmdlet. Specify the following settings:

* Set the $tape variable as the TapeMedium parameter value.
* Specify the Server parameter value.
* Specify the Path parameter value.
* Provide the AddDependentMediumAutomatically parameter.
* Provide the Security parameter.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)


