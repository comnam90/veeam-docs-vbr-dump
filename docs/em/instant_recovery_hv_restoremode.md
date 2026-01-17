---
title: "Step 3. Select Recovery Mode"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/instant_recovery_hv_restoremode.html"
last_updated: "9/4/2025"
product_version: "13.0.1.1071"
---


In this article

At the Restore mode step, select a recovery mode for the VM.

* Select Restore to the original location to recover the VM with initial settings to the original location. If this option is selected, you will pass directly to the [Summary](instant_recovery_hv_summary.md) step of the wizard.

|  |
| --- |
| Important |
| If you recover a VM with the original settings, and the original VM still exists in the virtual infrastructure, the original VM will be removed. |

* Select Restore to a new location or with different settings to recover the VM to a new location, or to any location but with different settings. If this option is selected, the Instant Recovery wizard will include additional steps for customizing VM settings.

![Step 3. Select Recovery Mode](images/instant_recovery_hv_restore_mode.webp "Selecting Recovery Mode")

Page updated 9/4/2025

Page content applies to build 13.0.1.1071
