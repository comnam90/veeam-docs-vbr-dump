---
title: "VBRVeeamDataCloudAssignedVault"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrveeamdatacloudassignedvault.html"
last_updated: "6/11/2025"
product_version: "13.0.1.1071"
---

# VBRVeeamDataCloudAssignedVault


Contains Veeam storage vault details.

Properties

| Property | Type | Description |
| --- | --- | --- |
| VaultId | String | Vault ID. |
| Name | String | Vault name. |
| StorageAccountName | String | Account used to connect to Veeam Data Cloud Vault. |
| StorageContainerName | String | Folder to keep |
| IsReadOnly | Boolean | Defines that the vault is in the the Active (read-only) status |
| ReadOnlyReason | String | Active (read-only) status reason. |

[Get-VBRVeeamDataCloudAssignedVault](get-vbrveeamdatacloudassignedvault.md)


