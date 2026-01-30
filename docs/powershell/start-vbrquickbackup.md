---
title: "Start-VBRQuickBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrquickbackup.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Start-VBRQuickBackup


Short Description

Performs quick backup.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRQuickBackup -VM <IVmItem[]> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts quick backup for a selected VMs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VM | Specifies the array of VMs for which you want to perform the QuickBackup.  You can add VMware or Hyper-V VMs. | Accepts the following objects:   * CViVmItem[] * CHvVmItem[]   To get these objects, run the following cmdlets:   * [Find-VBRViEntity](find-vbrvientity.md) * [Find-VBRHvEntity](find-vbrhventity.md) | True | Named | True (ByValue, |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRsession](vbrsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting QuickBackup for Single VM

|  |  |
| --- | --- |
| This example shows how to start quick backup for the SQL\_Database VM.  |  | | --- | | $VM = Find-VBRViEntity -Name "SQL\_Database"  Start-VBRQuickBackup -VM $VM |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $VM variable. 2. Run the Start-VBRQuickBackup cmdlet. Set the $VM variable as the VM parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting QuickBackup for Group of VMs

|  |  |
| --- | --- |
| This example shows how to start quick backup for a group of VMs.  |  | | --- | | $VMs = @()  $VMs += Find-VBRViEntity -Name "VM01"  $VMs += Find-VBRViEntity -Name "VM02"  Start-VBRQuickBackup -VM $VMs |  Perform the following steps:   1. Create an empty array. Declare the VMs variable and assign the @() to it. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Use the += operator to save the result to the $VMs variable. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Use the += operator to save the result to the $VMs variable. 4. Run the Start-VBRQuickBackup cmdlet. Set the $VMs variable as the VM parameter value. |

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Find-VBRHvEntity](find-vbrhventity.md)


