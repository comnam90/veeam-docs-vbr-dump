---
title: "Restoring VM Disk Data"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_encryption_vm_restore.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Restoring VM Disk Data


The process of restoring an Azure VM whose disks are encrypted with SSE or ADE does not differ from the same process for a VM with unencrypted disks.

Server-Side Encryption of Azure Disk Storage

During [entire VM restore](azure_entire_vm_restore_ui.md) or [disk restore](azure_performing_disk_restore.md), Veeam Backup for Microsoft Azure uses different key management options to encrypt the restored disks depending on the target Azure region:

* When performing restore to the original Azure region, Veeam Backup for Microsoft Azure encrypts the restored VM disks using the original key management option. However, if the associated Azure Key Vault or Disk Encryption Set is missing, the restored VM disks will be encrypted with platform-managed keys.
* When performing restore to a new Azure region, Veeam Backup for Microsoft Azure always encrypts the restored VM disks with platform-managed keys.

During [file-level recovery](azure_performing_flr.md), Veeam Backup for Microsoft Azure restores data as is; when performing restore to the original location, Veeam Backup for Microsoft Azure does not change the SSE settings configured for the VM.

Azure Disk Encryption

During entire VM restore or disk restore, Veeam Backup for Microsoft Azure preserves the original encryption settings for the restored VM disks. However, if the original Azure Key Vault is unavailable or the original Key Vault key is missing, Veeam Backup for Microsoft Azure will not be able to restore the data.

|  |
| --- |
| Important |
| If virtual disks of an Azure VM are encrypted using Azure Disk Encryption, the following limitations apply:   * Entire VM restore and disk restore are supported within one Azure region only. If you choose to back up or restore your data to another region, you must first migrate to the target region all Azure key vaults, cryptographic keys and secrets used to encrypt the source Azure resources, as described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/key-vault/general/move-region). * Restoring and browsing guest OS files on disks encrypted using the BitLocker and DM-Crypt features (as well as any custom disk encryption tools) is not supported. That is why you cannot perform file-level recovery. |

Page updated 2025-09-08

