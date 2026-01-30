---
title: "Step 1. Generate Answer File"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_vbr_linux_generate.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Step 1. Generate Answer File


To generate the answer file, do the following:

1. Log in to the host management console.
2. Click Remote Access Configuration.
3. Click Enter Shell.
4. Run the following command to generate the answer file. In the generate parameter, specify the path where the answer file will be saved.

|  |
| --- |
| dotnet /opt/veeam/vbr/Veeam.Backup.Configuration.UnattendedRestore.dll /generate:/var/lib/veeam/unattended.xml |

After you execute the command, the answer file will be generated with default preferences by the path you specified. You can manually edit the file to specify the necessary parameters.


