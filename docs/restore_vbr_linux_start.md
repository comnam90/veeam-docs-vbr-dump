---
title: "Step 3. Start Restore Process"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_vbr_linux_start.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Step 3. Start Restore Process


To start  the configuration database restore process, do the following:

1. Log in to the host management console.
2. Click Remote Access Configuration.
3. Click Enter Shell.
4. Use the following command to restore the configuration file. In the file parameter, specify the path where the configuration file is stored.

|  |
| --- |
| dotnet /opt/veeam/vbr/Veeam.Backup.Configuration.UnattendedRestore.dll /file:/var/lib/veeam/unattended.xml |

Veeam Backup & Replication will use the preferences specified in the unattended.xml file to perform the configuration database restore.


