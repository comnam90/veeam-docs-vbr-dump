---
title: "Uninstalling Veeam Plug-In for SAP MaxDB"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_uninstall.html"
last_updated: "10/28/2025"
product_version: "13.0.1.1071"
---

# Uninstalling Veeam Plug-In for SAP MaxDB

In this article

To uninstall Veeam Plug-In for SAP MaxDB, go to the directory with the Veeam Plug-In package and run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| rpm -e VeeamPluginforSAPMaxDB |

1. To uninstall the veeam-openssl3 package:

|  |
| --- |
| rpm -e veeam-openssl3-3.0.0.31-1.x86\_64 |

Note that these operations requires root privileges.

Page updated 10/28/2025

Page content applies to build 13.0.1.1071
