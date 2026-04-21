---
title: "Veeam Plug-Ins"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_plugins.html"
last_updated: "4/17/2026"
product_version: "13.0.1.2067"
---

# Veeam Plug-Ins


Veeam Plug-Ins

The machine where Veeam Plug-Ins will run must meet system requirements described in section [Backup Infrastructure](system_requirements_backup_server.md). Additionally, the following software must be installed:

Veeam Plug-Ins

| Veeam Plug-In | Software |
| Veeam Plug-In for AWS version 13.10.0.xxx and later | Microsoft .NET Core Runtime 8.0.25  Microsoft ASP.NET Core Shared Framework 8.0.25  For other system requirements of the plug-in, see [Workloads](platform_support_aws.md). |
| Veeam Plug-In for Microsoft Azure version 13.8.1.xxx and later | Microsoft .NET Core Runtime 8.0  Microsoft ASP.NET Core Shared Framework 8.0  For other system requirements of the plug-in, see [Workloads](platform_support_azure.md). |
| Veeam Plug-In for Google Cloud version 13.0.0.xxx and later1 | Microsoft .NET Core Runtime 8.0 or later  Microsoft ASP.NET Core Shared Framework 8.0 or later  For other system requirements of the plug-in, see [Workloads](platform_support_google.md). |
| Veeam Plug-In for Nutanix AHV version 13.9.0.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Plug-In for Nutanix AHV User Guide](https://helpcenter.veeam.com/docs/vbahv/userguide/system_requirements.html?ver=9). |
| Veeam Plug-In for oVirt KVM version 13.7.0.xxx and later1 | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Plug-In for oVirt KVM User Guide](https://helpcenter.veeam.com/docs/vbrhv/userguide/system_requirements.html?ver=7). |
| Veeam Plug-In for Proxmox Virtual Environment version 13.3.0.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Plug-In for Proxmox VE User Guide](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/system_requirements.html?ver=3). |
| Veeam Plug-in for Scale Computing HyperCore version 13.2.0.xxx | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Plug-in for Scale Computing HyperCore User Guide](https://helpcenter.veeam.com/docs/vpsch/userguide/system_requirements.html?ver=2). |
| Veeam Plug-In for Kasten version 13.2.1.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Kasten Integration Guide](https://helpcenter.veeam.com/docs/vbr/kasten_integration/system_requirements.html?ver=13). |

1 These plug-ins work only with Microsoft Windows-based backup servers.

|  |
| --- |
| Important |
| If the version of Microsoft .NET Core Runtime differs from the version of Microsoft ASP.NET Core Shared Framework, Veeam Plug-Ins will not be able to start. |


