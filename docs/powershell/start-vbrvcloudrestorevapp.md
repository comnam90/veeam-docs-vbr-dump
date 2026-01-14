---
title: "Start-VBRvCloudRestoreVApp"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcloudrestorevapp.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Start-VBRvCloudRestoreVApp

In this article

Short Description

Starts a vApp restore.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a vApp restore to another location or with different settings.

|  |
| --- |
| Start-VBRvCloudRestoreVApp -RestoreParams <CVcdVAppRestoreSettings> [-PowerUp] [-Reason <string>] [-RunAsync]  [<CommonParameters>] |

* Start a vApp restore to the original location.

|  |
| --- |
| Start-VBRvCloudRestoreVApp -RestorePoint <COib> [-PowerUp] [-Reason <string>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session for a selected vApp.

With this cmdlet, you can restore the vApp to the original location or to another location, or with different settings.

To restore the vApp to the original location you only need to indicate the desired restore point. Be careful to specify the restore point of the vApp, not an individual VM which is not a valid value for this cmdlet. Veeam Backup & Replication gets all the information needed for restore from the restore point data.

To run restore to another location or with different settings you need to first create a CVcdVAppRestoreSettings object which unifies all the settings options required for restore. The CVcdVAppRestoreSettings object is created with the help of the [New-VBRvCloudVAppRestoreSettings](new-vbrvcloudvapprestoresettings.md) cmdlet. See the [New-VBRvCloudVAppRestoreSettings](new-vbrvcloudvapprestoresettings.md) topic for detailed instructions for [advanced setup options](new-vbrvcloudvapprestoresettings.md#advanced_setup).

This cmdlet provides two scenarios for each case.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestoreParams | Specifies the CVcdVAppRestoreSettings object containing all settings required for the vApp restore. | Accepts the CVcdVAppRestoreSettings object. To create this object, run the [New-VBRvCloudVAppRestoreSettings](new-vbrvcloudvapprestoresettings.md) cmdlet. | True | 1 | True (ByValue, |
| RestorePoint | Specifies the restore point of the vApp. Used to restore vApp with all the same settings unchanged. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | False | Named | False |
| PowerUp | If set, the vApp will be powered up right after it is restored. Otherwise you will need to power up the vApp manually. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected vApp.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting vApp Restore to Original Location

|  |  |
| --- | --- |
| This example shows how to start a vApp restore. The vApp named vApp\_01 is restored to the original location and with all settings unchanged.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "vApp\_01"  Start-VBRvCloudRestoreVApp -RestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCloudRestoreVApp cmdlet. Set the $restorepoint variable as the RestorePoint variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting vApp Restore to Another Location

|  |  |
| --- | --- |
| This example shows how to restore a vApp to another location. The vApp named vApp\_01 is restored to the Org\_02 organization with all other settings remaining unchanged.  |  | | --- | | $backup = Get-VBRBackup -Name "vCloud"  $restoreparams = Get-VBRRestorePoint -Backup $backup | Where {$\_.Name -eq "vApp\_01"} | New-VBRvCloudVAppRestoreSettings  $restoreparams.OrgVdc = Find-VBRvCloudEntity -OrganizationVdc -Name "Org\_02"  Start-VBRvCloudRestoreVApp -RestoreParams $restoreparams -RunAsync |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. To restore the vApp to another organization, you need to first customize the CVcdVAppRestoreSettings object:  * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Pass the result to the Where-Object cmdlet to select the restore points with the Name property that equals vApp\_01. * Pipe the cmdlet output to the [New-VBRvCloudVAppRestoreSettings](new-vbrvcloudvapprestoresettings.md) cmdlet. Save the result to the $restoreparams variable.  1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the OrganizationVdc parameter. Specify the Name parameter value for the target organization. Save the result to the OrgVdc property of the $restoreparams variable.  1. Run the Start-VBRvCloudRestoreVApp cmdlet. Set the $restoreparams variable as the RestoreParams parameter value. Provide the RunAsync parameter. |

Related Commands

* [New-VBRvCloudVAppRestoreSettings](new-vbrvcloudvapprestoresettings.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
