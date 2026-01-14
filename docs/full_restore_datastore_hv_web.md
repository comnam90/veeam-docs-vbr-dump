---
title: "Step 5. Select Target Datastores"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/full_restore_datastore_hv_web.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Step 5. Select Target Datastores

In this article

The Datastore step of the wizard is available if you have selected Restore to a new location, or with different settings at the [Restore Mode](full_restore_mode_hv_web.md) step.

To specify a path to the folder where VM configuration files and disks will be stored:

1. Select the necessary files in the list and click Path.
2. In the Select Folder window, specify an existing folder, a new folder or a path to an SMB3 shared folder where VM files will be stored. The SMB share path must be specified in the UNC format, for example: \\172.16.11.38\Share01.

|  |
| --- |
| Important |
| The host or cluster on which you register VMs must have access to the specified SMB3 shared folder. If you are using SCVMM 2012 or later, the server hosting the Microsoft SMB3 shared folder must be registered in SCVMM as a storage device. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/previous-versions/system-center/system-center-2012-R2/jj614620%28v%3Dsc.12%29). |

1. Click OK.

[![Select Target Datastore - Web UI](images/full_restore_datastore_hv_web.webp)](images/full_restore_datastore_hv_web.webp "Select Target Datastore - Web UI")

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
