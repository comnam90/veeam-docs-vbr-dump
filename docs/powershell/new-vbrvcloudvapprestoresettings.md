---
title: "New-VBRvCloudVAppRestoreSettings"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvcloudvapprestoresettings.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# New-VBRvCloudVAppRestoreSettings


Short Description

Creates a set of vApp restore parameters.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRvCloudVAppRestoreSettings -RestorePoint <COib> [-vAppName <String>] [-OrgVdc <IVcdItem>] [-PowerUp] [-Reason <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet is an assistant command creating a CVcdVAppRestoreSettings object that is further used in the [Start-VBRvCloudRestoreVApp](start-vbrvcloudrestorevapp.md) cmdlet. This object gathers the parameters of a selected vApp that will be needed for restore.

The vApp that you want to restore and its parameters are derived from the specified restore point data. Use the OrgVdc parameter to set another organization where you want to restore the vApp to.

You can customize any of the parameters that are derived from the restore point. For more information, see the [Advanced Setup](#advanced_setup) section.

Advanced Setup

The restore parameters include the settings of the vApp, namely restore point, vApp name, organization VDC, and VMs included, as well as the settings of the VM: restore point, storage profile, datastore and template. Each of these settings can be reset to user settings allowing to restore the vApp i.e. to another organization, or with another vApp name, or apply other storage profiles to the VMs.

When applying different restore settings, it is recommended to set "null" to all VM settings that you leave unchanged to avoid conflicts when restoring the vApp to another infrastructure. For example, if the target organization has no access to the datastore that is originally set for the vApp, PowerShell will terminate your vApp restore job.

If you set null to all VM settings, Veeam Backup & Replication will apply the default settings of the target organization.

Make sure that you set the parameters for all VMs that belong to the vApp, otherwise you will not be able to run the restore job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the vApp you want to restore the vApp to. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, |
| vAppName | Specifies the name of the restored vApp. Use this parameter in case you want to restore the vApp with different name. | String | False | Named | False |
| OrgVdc | Specifies the organization VDC you want to restore the vApp to. If not set, the vApp will be restored to the original organization VDC. | Accepts the IVcdItem object. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet to get this object. | False | Named | False |
| PowerUp | If set to True, the vApp will be powered up right after it is restored. Otherwise, you will need to power up the vApp manually. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected vApp.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CVcdVAppRestoreSettings

Examples

Creating Settings for Future Restore of vApp

This command creates settings for the future restore of the vApp in another organization VDC.

* The $restorepoint variable contains the restore point of the vApp. The restore point is obtained with [Get-VBRRestorePoint](get-vbrrestorepoint.md) and assigned to the variable beforehand.
* The $vdc variable contains the organization VDC object where the vApp will be restored. The VDC object is obtained with [Find-VBRvCloudEntity](find-vbrvcloudentity.md) ([-OrganizationVdc]) and assigned to the variable beforehand.
* The PowerUp parameter is set to True to start the vApp automatically right after the restore.

|  |
| --- |
| $restoreparams = New-VBRvCloudVAppRestoreSettings -RestorePoint $restorepoint -vAppName "vApp01" -OrgVdc $Org |

Here you get the $restorepoint variable containing the vApp settings:

* vAppOib - the restore point of the vApp
* OrgVdc - the organization vDataCenter where the vApp is registered
* Vms - the list of VMs whithin the vApp
* vAppName - the name of the vApp

|  |
| --- |
| vAppOib          OrgVdc            Vms              vAppName -------          ------            ---              -------- Veeam.Bacvup..   Veeam.Backup... {Veeam.Backup...   vApp01 |

You can view the properties of the VMs within the vApp by typing $restoreparams.vms:

* VmOib - the VM restorepoint
* StorageProfile - the VM storage profile
* vCloudDatastore - the datastore that the VM uses
* VmTemplate - the VM template

|  |
| --- |
| VmOib      StorageProfile    vCloudDatastore        VmTemplate -----      --------------    ---------------        ---------- Veeam...   Name: 'Storag...  Veeam.Backup.CV... |

You need to specify the new organization to where you want to restore the vApp. The new organization object is assigned to the $org variable. All other VM parameters are set to null.

|  |
| --- |
| $restoreparams = New-VBRvCloudVAppRestoreSettings -RestorePoint $restorepoint -OrgVdc $Org  $restoreparams.vms[0].vCloudDatastore=$null  $restoreparams.vms[0].StorageProfile=$null  $restoreparams.vms[0].VmTemplate=$null |

The $restoreparams variable now contains the data needed for the restore and can be used in the [Start-VBRvCloudRestoreVApp](start-vbrvcloudrestorevapp.md) cmdlet.

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md) ([-OrganizationVdc])


