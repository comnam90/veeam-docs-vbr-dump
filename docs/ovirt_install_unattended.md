---
title: "Installing Veeam Plug-In for oVirt KVMin Unattended Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_install_unattended.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Installing Veeam Plug-In for oVirt KVMin Unattended Mode


You can install Veeam Plug-in for oVirt KVM in the unattended mode using the command line interface. The unattended installation mode does not require user interaction — the installation runs automatically in the background, and you do not have to respond to the installation wizard prompts. You can use the unattended installation mode to automate the plug-in installation process in large-scale environments.

To install Veeam Plug-in for oVirt KVM in the unattended mode, use either of the following options:

* If the plug-in is a part of Veeam Backup & Replication installation package, follow the instructions provided in section [Installing Veeam Backup & Replication in Unattended Mode](silent_mode_vbr.md).
* If the plug-in is delivered as a separate .EXE file, follow the instructions provided in this section.

Before You Begin

Before you start unattended installation, do the following:

1. Download the KVMPlugin\_13.7.0.473.exe file as described in section [Installing oVirt KVM Plug-In](ovirt_install_plugin.md) (steps 1-3).
2. Check compatibility of the Veeam Plug-in for oVirt KVM and Veeam Backup & Replication versions. For more information, see [System Requirements](ovirt_system_requirements.md).

Installation Command-Line Syntax

Open the command prompt and run the .EXE file using the following parameters:

|  |
| --- |
| %path% /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware |

The following command-line parameters are used to run the setup file:

| Parameter | Required | Description |
| --- | --- | --- |
| %path% | Yes | Specifies a path to the installation .EXE file on the backup server or in a network shared folder. |
| /silent | Yes | Sets the user interface level to None, which means no user interaction is needed during installation. |
| /accepteula | Yes | Confirms that you accept the terms of the Veeam license agreement. |
| /acceptthirdpartylicenses | Yes | Confirms that you accept the license agreement for 3rd party components that Veeam incorporates. |
| /acceptlicensingpolicy | Yes | Confirms that you accept the Veeam licensing policy. |
| /acceptrequiredsoftware | Yes | Confirms that you accept the license agreements for each required software that Veeam will install. |
| /uninstall | No | Uninstalls the plug-in. |
| /repair | No | Replaces missing files and firewall rules. |

Examples

The following command installs the plug-in:

|  |
| --- |
| KVMPlugin\_13.7.0.473.exe /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware |

The following command repairs the plug-in:

|  |
| --- |
| KVMPlugin\_13.7.0.473.exe /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware /repair |

The following command uninstalls the plug-in:

|  |
| --- |
| KVMPlugin\_13.7.0.473.exe /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware /uninstall |

Veeam Plug-in for oVirt KVM provides the following status codes to report about the installation result:

| Code | Description |
| --- | --- |
| 0 | plug-in installation has successfully completed. |
| 1603 | plug-in installation has failed. |
| 3010 | plug-in installation has successfully completed. The backup server requires rebooting. |

|  |
| --- |
| Tip |
| For detailed logs of plug-in installation, navigate to the Program Data\Veeam\Setup\Temp\ folder on the backup server and view the following files:   * VeeamPluginBootstrap.log * KVMPluginSetup.log * KVMPluginUISetup.log * KVMPluginProxySetup.log |


