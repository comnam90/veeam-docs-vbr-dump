---
title: "Installing Veeam Plug-In for Sangfor aSV in Unattended Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_install_unattended.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Installing Veeam Plug-In for Sangfor aSV in Unattended Mode


You can install Veeam Plug-in for Sangfor aSV in the unattended mode using the command line interface. The unattended installation mode does not require user interaction — the installation runs automatically in the background, and you do not have to respond to the installation wizard prompts. You can use the unattended installation mode to automate the Veeam Plug-in for Sangfor aSV installation process in large-scale environments.

Before You Begin

Before you start unattended installation, do the following:

1. Download the .exe file as described in section [Deployment](sangfor_deployment.md#install) (steps 1-3).
2. Check compatibility of the Veeam Plug-in for Sangfor aSV and Veeam Backup & Replication versions. For more information, see [System Requirements](sangfor_system_requirements.md).

Installation Command-Line Syntax

Open the command prompt and run the .EXE file using the following parameters:

|  |
| --- |
| %path% /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware |

The following command-line parameters are used to run the setup file:

Installation Command-Line Syntax

| Parameter | Required | Description |
| %path% | Yes | Specifies a path to the installation .EXE file on the backup server or in a network shared folder. |
| /silent | Yes | Sets the user interface level to None, which means no user interaction is needed during installation. |
| /accepteula | Yes | Confirms that you accept the terms of the Veeam license agreement. |
| /acceptthirdpartylicenses | Yes | Confirms that you accept the license agreement for 3rd party components that Veeam incorporates. |
| /acceptlicensingpolicy | Yes | Confirms that you accept the Veeam licensing policy. |
| /acceptrequiredsoftware | Yes | Confirms that you accept the license agreements for each required software that Veeam will install. |
| /uninstall | No | Uninstalls the plug-in. |
| /repair | No | Replaces missing files and firewall rules. |

Examples

The following command installs Veeam Plug-in for Sangfor aSV:

|  |
| --- |
| VeeamPluginSFR\_13.1.0.358.exe /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware |

The following command repairs Veeam Plug-in for Sangfor aSV:

|  |
| --- |
| VeeamPluginSFR\_13.1.0.358.exe /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware /repair |

The following command uninstalls Veeam Plug-in for Sangfor aSV:

|  |
| --- |
| VeeamPluginSFR\_13.1.0.358.exe /silent /accepteula /acceptthirdpartylicenses /acceptlicensingpolicy /acceptrequiredsoftware /uninstall |

Veeam Plug-in for Sangfor aSV provides the following status codes to report about the installation result:

Examples

| Code | Description |
| 0 | Veeam Plug-in for Sangfor aSV installation has successfully completed. |
| 1603 | Veeam Plug-in for Sangfor aSV installation has failed. |
| 3010 | Veeam Plug-in for Sangfor aSV installation has successfully completed. The backup server requires rebooting. |

|  |
| --- |
| Tip |
| For detailed logs of the Veeam Plug-in for Sangfor aSV installation, navigate to the Program Data\Veeam\Setup\Temp\ folder on the backup server and view the following files:   * VeeamPluginBootstrap.log * VeeamPluginSFR.log * VeeamPluginSFRUI.log * VeeamPluginSFRWorker.log |

Page updated 2026-07-28

