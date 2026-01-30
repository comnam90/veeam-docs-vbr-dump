---
title: "Start-VBRNASInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrnasinstantrecoverymigration.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Start-VBRNASInstantRecoveryMigration


Short Description

Starts migration to production for the running instant file share recovery session.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start migration to production for the NAS instant recovery session to the original location.

|  |
| --- |
| Start-VBRNASInstantRecoveryMigration -InstantRecovery <VBRNASInstantRecovery> [-ReplaceAll] -SwitchOverOptions <VBRNASInstantRecoveryMigrationSwitchOverOptions> [-RunAsync]  [<CommonParameters>] |

* Start migration to production for the NAS instant recovery session to a different location.

|  |
| --- |
| Start-VBRNASInstantRecoveryMigration -InstantRecovery <VBRNASInstantRecovery> -NASServer <VBRUnstructuredServer> [-Path] <String> [-ReplaceAll] -SwitchOverOptions <VBRNASInstantRecoveryMigrationSwitchOverOptions> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts migration to production for the running instant file share recovery session. It supports migration to the original or different location.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies an instant recovery session. The cmdlet will start migration to production for this session. | Accepts the [VBRNASInstantRecovery](vbrnasinstantrecovery.md) object. To get this object, run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| NASServer | Specifies a server where the mounted file share will be migrated to production.  This parameter is specified for the migration to a different location type. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | 1 | False |
| Path | Specifies a path at the NASServer where the mounted file share will be migrated to production.  This parameter is specified for the migration to a different location type. | String | True | 2 | False |
| ReplaceAll | Enables the Replace All option.  If you provide this parameter, the cmdlet will restore the whole file share and overwrite the existing files with the restored files.  Otherwise, the cmdlet will overwrite the existing files only if they are older than the restored files. | SwitchParameter | False | Named | False |
| RunAsync | Defines  that the command returns immediately without waiting for the task to complete.  Note: If the switchover is started with option Manual or Scheduled, the cmdlet will wait endlessly or for a long time. Before starting waiting, the cmdlet will display a warning. | SwitchParameter | False | Named | False |
| SwitchOverOptions | Specifies switchover options for the specified instant recovery session. The cmdlet will start migration to production for the session with the specified switchover options. | Accepts the VBRNASInstantRecoveryMigrationSwitchOverOptions object. To create this object, run the [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASInstantRecoveryMigration](vbrnasinstantrecoverymigration.md) object that defines settings of the migration to production session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting File Share Migration to Original Location

|  |  |
| --- | --- |
| This command starts the file share migration to the original location.  |  | | --- | | $nasInstantRecovery = Get-VBRNASInstantRecovery -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  $switchover = New-VBRNASInstantRecoveryMigrationSwitchOverOptions -Auto  Write-Output "Start File Share Migration."  Write-Output $nasInstantRecovery  Start-VBRNASInstantRecoveryMigration -InstantRecovery $nasInstantRecovery -SwitchOverOptions $switchover |  Perform the following steps:   1. Run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $nasInstantRecovery variable. 2. Run the [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md) cmdlet. Provide the Auto parameter. Save the result to the $switchover variable. 3. Run the Write-Output cmdlet. Specify the output wording. 4. Run the Write-Output cmdlet. Provide the $nasInstantRecovery variable. 5. Run the Start-VBRNASInstantRecoveryMigration cmdlet. Set the $nasInstantRecovery variable as the InstantRecovery parameter value. Set the $switchover variable as the SwitchOverOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting File Share Migration to Different Location

|  |  |
| --- | --- |
| This command starts the file share migration to a location different from the original one.  |  | | --- | | $nasInstantRecovery = Get-VBRNASInstantRecovery -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  $nasServer = Get-VBRUnstructuredServer -Name "\\server\original\_folder"  $switchover = New-VBRNASInstantRecoveryMigrationSwitchOverOptions -Auto  Write-Output "Start File Share Migration."  Write-Output $nasInstantRecovery  Start-VBRNASInstantRecoveryMigration -InstantRecovery $nasInstantRecovery -NASServer $nasServer -Path "\\server\original\_folder\new\_folder" -SwitchOverOptions $switchover |  Perform the following steps:   1. Run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $nasInstantRecovery variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter. Save the result to the $nasServer variable. 3. Run the [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md) cmdlet. Provide the Auto parameter. Save the result to the $switchover variable. 4. Run the Write-Output cmdlet. Specify the output wording. 5. Run the Write-Output cmdlet. Provide the $nasInstantRecovery variable. 6. Run the Start-VBRNASInstantRecoveryMigration cmdlet. Specify the following settings:  * Set the $nasInstantRecovery variable as the InstantRecovery parameter value. * Set the $nasServer variable as the NASServer parameter value. * Specify the Path parameter value. * Set the $switchover variable as the SwitchOverOptions parameter value. |

Related Commands

* [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md)


