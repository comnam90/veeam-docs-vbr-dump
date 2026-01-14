---
title: "Installing Plug-In on Oracle Solaris"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/install_plugin_unix.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Installing Plug-In on Oracle Solaris

In this article

Veeam Plug-In for Oracle RMAN is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

|  |
| --- |
| Important |
| Consider the following:   * Veeam Plug-In must be installed on the Oracle Database server. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories. |

To install Veeam Plug-In for Oracle RMAN on an Oracle Solaris machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. In the installation disk folder, navigate to one of the following folders depending on your system:

* For i386: \Plugins\Oracle RMAN\Solaris\i386.
* For SPARC: \Plugins\Oracle RMAN\Solaris\SPARC.

1. Upload the following Veeam Plug-In package depending on your system to the Oracle server:

* For i386: VeeamPluginforOracleRMAN-13.0.1.180-1.i386.pkg.
* For SPARC: VeeamPluginforOracleRMAN-13.0.1.180-1.SPARC.pkg.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for Oracle RMAN from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive, navigate to one of the following folders depending on your system:

* For i386: \VeeamPluginforOracleRMAN-13.0.1.180\RMANSolaris\i386.
* For SPARC: \VeeamPluginforOracleRMAN-13.0.1.180\RMANSolaris\SPARC.

1. Upload the following Veeam Plug-In package depending on your system to the Oracle server:

* For i386: VeeamPluginforOracleRMAN-13.0.1.180-1.i386.pkg.
* For SPARC: VeeamPluginforOracleRMAN-13.0.1.180-1.SPARC.pkg.

1. Install the plug-in from package with root privileges. Make sure the root user has privileges to add the PKG file.

|  |
| --- |
| pkgadd -d /tmp/VeeamPluginforOracleRMAN-13.0.1.180-1.pkg |

Once Veeam Plug-In is installed, you can configure the plug-in settings. For details, see [Configuring Plug-In on Linux or Unix](configuring_rman_plugin_lin.md).

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
