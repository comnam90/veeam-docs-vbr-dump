---
title: "Start-VBRTapeRestoreFiles (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtaperestorefiles.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Start-VBRTapeRestoreFiles (obsolete)

In this article

Short Description

Starts files restore from tape.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but it is recommended to perform the tape restore operation with Veeam Backup & Replication UI for full functionality |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Start-VBRTapeRestoreFiles [-Files <CatalogueFile[]>] [-Version <CatalogueFileVersion[]>] -Server <CHost> -Path <String> [-PreserveHierarhy] [-Overwrite <RestoreOverwrite>] [-Security] [-RunAsync] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restoring files from backup copied to tape. You can restore file to its most recent state or to any of its backup version. The versions of files are used as restore points.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Files | Specifies the files to restore. The most recent file version is used. | Accepts the CatalogueFile[] object. To get this object, run the [Find-VBRTapeCatalog](find-vbrtapecatalog.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Version | Specifies the version of the files you want to restore. | Accepts the CatalogueFileVersion[] object. To get this object, run the [Find-VBRTapeCatalogVersion](find-vbrtapecatalogversion.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Server | Specifies the source host where the files to restore are located. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the files to restore. | String | True | Named | False |
| Preserve Hierarhy | If indicated, the files and folders will be restored in respect to the original folder hierarchy. Otherwise all files and folders are restored into a plain sequence. | SwitchParameter | False | Named | False |
| Overwrite | Specifies the overwrite options in case the file exists on the target side:   * None - leave the original file * Newer - overwrite the file if the restore file in newer * Always - overwrite the existing file | RestoreOverwrite | False | Named | False |
| Security | If indicated, the files will be restored with with the original security settings. Otherwise the file/folder security settings will be inherited from parent item. | SwitchParameter | False | Named | True (ByValue, ByProperty Name) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring File from Tape [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to start restoring the VM01 Backup Job 1.vbm file.  |  | | --- | | $server = Get-VBRServer -Name "srv001"  Find-VBRTapeCatalog -Name "VM01 Backup Job 1.vbm" | Start-VBRTapeRestoreFiles -Server $server -Path "C:\backup\Backup Job 1\VM01 Backup Job 1.vbm" -PreserveHierarhy -Overwrite Newer -Security -RunAsync |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRTapeCatalog](find-vbrtapecatalog.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Start-VBRTapeRestoreFiles cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Provide the PreserveHierarhy parameter value. * Set the Newer option for the Overwrite parameter. * Provide the Security parameter value. * Provide the RunAsync parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Specific Version of File from Tape [Using Variable]

|  |  |
| --- | --- |
| This example shows how to restore a specific version of the VM01 Backup Job 1.vbm file.  |  | | --- | | $file = Find-VBRTapeCatalog -Name "VM01 Backup Job 1.vbm"  $fileversion = Find-VBRTapeCatalogVersion -CatalogFile $file  $server = Get-VBRServer -Name "srv001"  Start-VBRTapeRestoreFiles -Version $fileversion -Server $server -Path "C:\backup\Backup Job 1\VM01 Backup Job 1.vbm" -PreserveHierarhy -Overwrite Always |  Perform the following steps:   1. Run the [Find-VBRTapeCatalog](find-vbrtapecatalog.md) cmdlet. Specify the Name parameter value. Save the result to the $file variable. 2. Run the [Find-VBRTapeCatalogVersion](find-vbrtapecatalogversion.md) cmdlet. Set the $file variable as the CatalogFile parameter value. Save the result to the $fileversion variable. 3. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 4. Pipe the cmdlet output to the Start-VBRTapeRestoreFiles cmdlet. Specify the following settings:  * Set the $fileversion variable as the Version parameter value.  * Set the $server variable as the Server parameter value.  * Specify the Path parameter value. * Provide the PreserveHierarhy parameter value. * Set the Always option for the Overwrite parameter. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRTapeCatalog](find-vbrtapecatalog.md)
* [Find-VBRTapeCatalogVersion](find-vbrtapecatalogversion.md)

Page updated 6/3/2024

Page content applies to build 13.0.1.1071
