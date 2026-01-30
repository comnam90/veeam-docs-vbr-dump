---
title: "Uninstalling Plug-In for SAP HANA"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uninstall_plugin_saphana.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# Uninstalling Plug-In for SAP HANA


To uninstall Veeam Plug-In for SAP HANA on a Linux machine, go to the directory with the Veeam Plug-In package and run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| rpm -e VeeamPluginforSAPHANA |

1. To uninstall the veeam-openssl3 package:

|  |
| --- |
| rpm -e veeam-openssl3-3.0.0.31-1.x86\_64 |

Note that these operations requires root privileges.


