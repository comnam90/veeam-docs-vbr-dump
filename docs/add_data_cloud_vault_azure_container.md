---
title: "Step 4. Choose Target Folder"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/add_data_cloud_vault_azure_container.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Choose Target Folder


After you choose a storage vault at step 3 of the wizard, Veeam Backup & Replication automatically detects both the Azure region where the vault is located and the storage account that is associated with it. The product also creates a new folder inside the container that will be used to group your backup files; you can use either this new folder or any other folder that already exists in the container — to do that, click Browse at the Container step.

|  |
| --- |
| Note |
| Veeam Backup & Replication does not support adding storage vaults with immutability disabled. That is why you will not be able to clear the Make backups immutable for the entire duration of their retention policy check box. For more information on the immutability feature, see [Immutability](azure_immutability.md). |

![Step 4. Choose Target Folder](images/external_vault_azure_container.webp)

Page updated 2026-07-28

