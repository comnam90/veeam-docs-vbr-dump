---
title: "Installing Plug-In on IBM AIX"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/install_plugin_aix.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Installing Plug-In on IBM AIX


Veeam Plug-In for Oracle RMAN is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

|  |
| --- |
| Important |
| Consider the following:   * Veeam Plug-In must be installed on the Oracle Database server. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories. |

To install Veeam Plug-In for Oracle RMAN on an IBM AIX machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. In the installation disk folder, go to \Plugins\Oracle RMAN\AIX\ppc64.
2. Upload the Veeam Plug-In installation package (VeeamPluginforOracleRMAN-13.0.1.180-1.aix6.1.ppc.rpm) to the AIX server where the target Oracle database is deployed.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for Oracle RMAN from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive, in the \VeeamPluginforOracleRMAN-13.0.1.180\RMAN\_AIX\ppc64 folder, find the VeeamPluginforOracleRMAN-13.0.1.180-1.aix6.1.ppc.rpm file.
3. Upload the Veeam Plug-In installation package (VeeamPluginforOracleRMAN-13.0.1.180-1.aix6.1.ppc.rpm) to the AIX server where the target Oracle database is deployed.

1. Install the plug-in from package with root privileges. Make sure the root user has privileges to add the PKG file.

|  |
| --- |
| rpm -i VeeamPluginforOracleRMAN-13.0.1.180-1.aix6.1.ppc.rpm |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Plug-In on Linux or Unix](configuring_rman_plugin_lin.md).


