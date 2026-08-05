---
title: "Uninstalling Plug-In"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_uninstall.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Uninstalling Plug-In


Installation scenario depends on the OS you work with:

* [Microsoft Windows](#win)
* [Linux](#linux)

* [IBM AIX](#aix)

Uninstalling Veeam Plug-In on Windows Machines

To uninstall Veeam Plug-In and undo the configuration changes, do the following:

1. Open the Control Panel and click Programs and Features.
2. In the list of programs, select Veeam Plug-In for IBM Db2 and click Uninstall.

Uninstalling Veeam Plug-In on Linux Machines

On a Linux machine, go to the directory with the Veeam Plug-In package and run the following command. Note that the operation requires root privileges.

For CentOS / RHEL / Oracle Linux, run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| rpm -e VeeamPluginforDB2 |

1. To uninstall the openssl-fips-redistributable-3.1.2 package:

|  |
| --- |
| rpm -e openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64 |

For SLES, run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| zypper rm VeeamPluginforDB2 |

1. To uninstall the openssl-fips-redistributable-3.1.2 package:

|  |
| --- |
| zypper rm openssl-fips-redistributable-3.1.2-3.1.2.2-1.x86\_64 |

For Ubuntu, run the following commands:

1. To uninstall Veeam Plug-In:

|  |
| --- |
| apt-get remove VeeamPluginforDB2 |

1. To uninstall the openssl-fips-redistributable-3.1.2 package:

|  |
| --- |
| apt-get remove openssl-fips-redistributable-3.1.2\_3.1.2.2\_amd64 |

Uninstalling Veeam Plug-In on IBM AIX Machines

To uninstall Veeam Plug-In and undo the configuration changes, run the following command. Note that the operation requires root privileges.

|  |
| --- |
| rpm -e VeeamPluginforDB2 |

Page updated 2026-07-28

