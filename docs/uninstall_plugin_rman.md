---
title: "Uninstalling Veeam Plug-In for Oracle RMAN"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uninstall_plugin_rman.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# Uninstalling Veeam Plug-In for Oracle RMAN

In this article

You can uninstall the Veeam Plug-In and undo the configuration changes made by Veeam Plug-In.

When you [configure Veeam Plug-In](configuring_rman_plugin.md), original settings of Oracle RMAN are saved in the /opt/veeam/VeeamPluginforOracleRMAN/RMANParameters.xml file (or in the %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\RMANParameters.xml for Windows). If you uninstall Veeam Plug-In for Oracle RMAN, original settings of Oracle RMAN are restored from the RMANParameters.xml file.

Uninstalling Veeam Plug-In on Linux or IBM AIX Machines

To uninstall Veeam Plug-In and undo the configuration changes, go to the directory with the Veeam Plug-In package and run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| rpm -e VeeamPluginforOracleRMAN |

1. [For Linux] To uninstall the veeam-openssl3 package:

|  |
| --- |
| rpm -e veeam-openssl3-3.0.0.31-1.x86\_64 |

Note that these operations requires root privileges.

Uninstalling Veeam Plug-In on Windows Machines

To uninstall Veeam Plug-In and undo the configuration changes, do the following:

1. Open the Control Panel and click Programs and Features.
2. In the list of programs, select Veeam Plug-In for Oracle RMAN and click Uninstall.

Uninstalling Veeam Plug-In on Solaris Machines

To uninstall Veeam Plug-In and undo the configuration changes, run the following command:

|  |
| --- |
| pkgrm VeeamPluginforOracleRMAN |

Page updated 9/11/2025

Page content applies to build 13.0.1.1071
