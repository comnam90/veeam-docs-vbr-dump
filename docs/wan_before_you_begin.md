---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/wan_before_you_begin.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you add a WAN accelerator, check the following prerequisites:

* The machine that will operate as a WAN accelerator must meet the system requirements. For more information, see [System Requirements](system_requirements.md#wan).

* You can assign the WAN accelerator role to a physical or virtual machine. The WAN accelerator role can be assigned to backup proxies and Microsoft Windows-based or Linux-based backup repositories already configured in the backup infrastructure.
* You must use 64-bit Microsoft Windows or Linux machines as WAN accelerators. 32-bit versions of Microsoft Windows or Linux machines are not supported for the WAN accelerator role.
* WAN acceleration operations are resource-consuming. When assigning the WAN accelerator role, consider available CPU and memory resources of the server. It is recommended that you assign the WAN accelerator role to servers with 8 GB RAM and more.

* The machine must have enough free disk space to store digests or global cache data. For more information, see [WAN Accelerator Sizing](wan_accelerator_sizing.md).
* You must add the machine to the Veeam Backup & Replication console as a managed server before adding it as a WAN accelerator.


