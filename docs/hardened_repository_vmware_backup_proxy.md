---
title: "Hardened Repository as VMware Backup Proxy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_vmware_backup_proxy.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Hardened Repository as VMware Backup Proxy


You can assign the VMware backup proxy role to the hardened repository. In this case, only the Network mode (NBD) is supported. Other transport modes will not be available for selection.

|  |
| --- |
| Note |
| A VMware backup proxy requires VMware VDDK components to be installed. This increases the risk of hardened repository attacks through VMware VDDK vulnerabilities. It is recommended to assign this role to another managed server when possible. |

To add a hardened repository as a VMware backup proxy, use the New VMware Proxy wizard. For more information, see [Adding VMware Backup Proxies](add_vmware_proxy.md).


