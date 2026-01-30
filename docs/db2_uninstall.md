---
title: "Uninstalling Plug-In"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_uninstall.html"
last_updated: "11/25/2025"
product_version: "13.0.1.1071"
---

# Uninstalling Plug-In


Installation scenario depends on the OS you work with:

* [Uninstalling Veeam Plug-In on Linux machines](#linux).

* [Unistalling Veeam Plug-In on IBM AIX machines](#aix).

Uninstalling Veeam Plug-In on Linux Machines

On a Linux machine, go to the directory with the Veeam Plug-In package and run the following command. Note that the operation requires root privileges.

For CentOS / RHEL / Oracle Linux, run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| rpm -e VeeamPluginforDB2 |

1. To uninstall the veeam-openssl3 package:

|  |
| --- |
| rpm -e veeam-openssl3-3.0.0.31-1.x86\_64 |

For SLES, run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| zypper rm VeeamPluginforDB2 |

1. To uninstall the veeam-openssl3 package:

|  |
| --- |
| zypper rm veeam-openssl3-3.0.0.31-1.x86\_64 |

For Ubuntu, run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| apt-get remove VeeamPluginforDB2 |

1. To uninstall the veeam-openssl3 package:

|  |
| --- |
| apt-get remove veeam-openssl3\_3.0.0.31\_amd64 |

Uninstalling Veeam Plug-In on IBM AIX Machines

To uninstall Veeam Plug-In and undo the configuration changes, run the following command. Note that the operation requires root privileges.

|  |
| --- |
| rpm -e VeeamPluginforDB2 |


