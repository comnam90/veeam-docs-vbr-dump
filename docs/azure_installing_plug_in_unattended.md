---
title: "Installing Plug-In in Unattended Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_installing_plug_in_unattended.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Installing Plug-In in Unattended Mode


You can install or uninstall Veeam Plug-in for Microsoft Azure in the unattended mode using the command line interface. The unattended mode does not require user interaction — the installation runs automatically in the background, and you do not have to respond to the installation wizard prompts. You can use it to automate processes in large-scale environments.

To install Veeam Plug-in for Microsoft Azure in unattended mode, use either of the following options:

* If Veeam Plug-in for Microsoft Azure is a part of Veeam Backup & Replication installation package, follow the instructions provided in [Installing Veeam Backup & Replication in Silent Mode](install_vbr_answer_file.md).
* If Veeam Plug-in for Microsoft Azure is delivered as a separate .EXE file, use the instructions from this subsection.

Before You Begin

Before you start unattended installation, do the following:

1. Download the Veeam Plug-in for Microsoft Azure .EXE file as described in section [Deploying Plug-In](azure_deploying_plug_in.md).
2. Check compatibility of Veeam Plug-in for Microsoft Azure and Veeam Backup & Replication versions. For more information, see [System Requirements](azure_system_requirements.md#compatibility).

Installation Command-Line Syntax

Open the command prompt and run the .EXE file using the following parameters:

|  |
| --- |
| %path% /silent /accepteula /acceptlicensingpolicy /acceptthirdpartylicenses /acceptrequiredsoftware [/uninstall] |

The following command-line parameters are used to run the setup file:

Installation Command-Line Syntax

| Parameter | Required | Description |
| %path% | Yes | Specifies a path to the installation .EXE file on the backup server or in a network shared folder. |
| /silent | Yes | Sets the user interface level to None, which means no user interaction is needed during installation. |
| /accepteula | Yes | Confirms that you accept the terms of the Veeam license agreement. |
| /acceptlicensingpolicy | Yes | Confirms that you accept the Veeam licensing policy. |
| /acceptthirdpartylicenses | Yes | Confirms that you accept the license agreement for 3rd party components that Veeam incorporates. |
| /acceptrequiredsoftware | Yes | Confirms that you accept the license agreements for each required software that Veeam will install. |
| /uninstall | No | Uninstalls the plug-in.  Example: ”AzurePlugin\_13.9.0.354.exe /silent /accepteula /acceptlicensingpolicy /acceptthirdpartylicenses /acceptrequiredsoftware /uninstall” |

Page updated 2026-07-31

