---
title: "Uninstalling Veeam Plug-In for SAP MaxDB"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_uninstall.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Uninstalling Veeam Plug-In for SAP MaxDB


To uninstall Veeam Plug-In for SAP MaxDB, go to the directory with the Veeam Plug-In package and run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| rpm -e VeeamPluginforSAPMaxDB |

1. To uninstall the openssl-fips-redistributable-3.1.2 package:

|  |
| --- |
| rpm -e openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64 |

Note that these operations requires root privileges.

Page updated 2026-07-28

