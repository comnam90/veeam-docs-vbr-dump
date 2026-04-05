---
title: "Step 3. Specify Veeam Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_data_cloud_account_web.html"
last_updated: "4/1/2026"
product_version: "13.0.1.2067"
---

# Step 3. Specify Veeam Account


At the Account step of the wizard, do the following:

1. [Register backup server with Veeam Data Cloud](#register).
2. [Specify storage vault settings](#vault).
3. [Specify the connection mode](#connectionmode).

Registering Backup Server with Veeam Data Cloud

To register the backup server with Veeam Data Cloud using your Veeam credentials, do the following:

1. Click the Change link. After that, the Backup Server Registration Code window will appear.
2. To the right of the Registration Code field, click Copy.
3. Click the Veeam Data Cloud Portal link. You will be moved to Veeam Data Cloud. Enter your Veeam credentials.

|  |
| --- |
| Note |
| Ensure that the email address you use matches the email address of the License Administrator. Consider that this email address is case-sensitive. If you plan to delegate access to another user, make sure that he also has the License Administrator role. |

1. In the Register New Product window, under the Registration Token filed, paste the registration code you have copied.
2. Click Register. The backup server will be registered with Veeam Data Cloud.

[![Step 3. Specify Veeam Account](images/veeam_vault_backup_server_code_web.webp)](images/veeam_vault_backup_server_code_web.webp)

Specifying Storage Vault Settings

To specify storage vault settings, do the following:

1. From the Vault drop-down list, select the storage vault that you want to use.
2. To manage vaults, click the Manage link.

|  |
| --- |
| Note |
| Consider the following:   * If you have only one storage vault that has not been associated with any backup server before, this vault will appear in the drop-down list automatically. * If you do not have any storage vaults associated with your backup server, the Vault drop-down list will be empty. For detailed instructions on how to assign a storage vault to your backup server, see the [Assigning Storage Vaults to Workloads](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#assigning-storage-vaults-to-workloads) section in the Veeam Data Cloud User Guide. After you add a storage vault and assign it to the backup server, click the refresh icon (![Step 3. Specify Veeam Account](images/refresh_icon.webp)). The vault will show up in the drop-down list. * Keep in mind that it might take several minutes to add a certificate (a public key) on the Microsoft Azure Entra ID side. |

Specifying Connection Mode

By default, Veeam Backup & Replication uses the Direct mode to transfer data to an object storage repository. To specify different connection settings, do the following:

1. Next to the Connection mode field, click Choose.
2. In the Connection Mode window, select one of the following:

* Direct — select this option if you want to instantly move data of processed VMs or file shares to object storage repositories. Before you select this option, check the following [Considerations and Limitations](object_storage_repository_cal.md#directmode).
* Through a gateway server — select this option if you want Veeam Backup & Replication to use gateway servers to transfer data from processed machines or file shares to object storage repositories. From the Name list, select gateway servers that you want to use for data transfer operations.

By default, the role of a gateway server is assigned to the Veeam Backup & Replication server. You can choose any Microsoft Windows or Linux server that is added to your backup infrastructure and has internet connection. Note that you must add the server to the backup infrastructure beforehand. Before you add the server, check the following [Considerations and Limitations](object_storage_repository_cal.md). For more information on how to add a server, see [Virtualization Servers and Hosts](setup_add_server.md).

[![Step 3. Specify Veeam Account](images/veeam_vault_credentials_authorization_web.webp)](images/veeam_vault_credentials_authorization_web.webp)


