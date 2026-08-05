---
title: "Data Encryption"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_data_encryption.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Data Encryption


By default, Azure Storage uses service-side encryption (SSE) to automatically encrypt data with 256-bit AES keys. For more information on Azure Storage encryption, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/common/storage-service-encryption?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&bc=%2Fazure%2Fstorage%2Fblobs%2Fbreadcrumb%2Ftoc.json).

For enhanced data security, Veeam Plug-in for Microsoft Azure allows you to encrypt backed-up data in repositories using Veeam encryption mechanisms. Additionally, Veeam Plug-in for Microsoft Azure supports native Microsoft Azure encryption of Azure VMs.

|  |
| --- |
| Note |
| Sensitive customer data (credentials of user accounts required to connect to virtual servers and other systems, cloud credentials, and so on) is stored in the configuration database in the encrypted format. |

In This Section

* [Repository Encryption](azure_repo_encryption.md)
* [Azure VM Disk Encryption](azure_vm_encryption.md)

Page updated 2026-07-01

