---
title: "Veeam Agent for Microsoft Windows Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protection_group_advanced_vaw.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# Veeam Agent for Microsoft Windows Settings

In this article

You can specify the following settings for Veeam Agent for Microsoft Windows that will be deployed on computers included in the protection group:

* Network usage settings. You can limit bandwidth consumption and restrict network connections usage for Veeam Agent for Microsoft Windows backup jobs. Limiting bandwidth consumption prevents jobs from utilizing the entire bandwidth available in your environment and makes sure that enough traffic is provided for other network operations. In addition to limiting bandwidth consumption, you can choose whether to allow backup over metered connections and VPN connections. For Microsoft Windows workstations that run Veeam Agent, you can also specify one or more wireless networks over which Veeam Agent is allowed to perform backup or restrict usage over any wireless networks.

To learn more, see the [Restricting Network Connections Usage](https://helpcenter.veeam.com/docs/agentforwindows/userguide/settings_network.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.

|  |
| --- |
| ![Veeam Agent for Microsoft Windows Settings](images/icon_important.webp) IMPORTANT |
| Network usage settings are not applied to protected computers added to a Veeam Agent backup job managed by the backup server. |

* Backup I/O settings. You can instruct Veeam Agent for Microsoft Windows to throttle its activities during backup. This option can help you avoid situations when backup tasks performed by Veeam Agent for Microsoft Windows consume all available hard disk resources and hinder work of other applications and services on a protected computer. With throttling enabled, Veeam Backup & Replication sets low priority for Veeam Agent components running on protected computers and engaged in the backup process. If this option is not enabled, Veeam Agent components have normal priority.
* Security settings. You can allow user accounts that do not have administrative privileges on a Veeam Agent computer to perform file-level restore on this computer.

|  |
| --- |
| ![Veeam Agent for Microsoft Windows Settings](images/icon_important.webp) IMPORTANT |
| Security settings are not applied to protected computers added to a Veeam Agent backup job managed by the backup server. |

Veeam Backup & Replication applies the specified settings to Veeam Agent that runs on a protected computer added to a backup policy. Veeam Backup & Replication applies the settings during the protection group rescan process. Settings are saved to the Veeam Agent for Microsoft Windows database on the protected computer.

To specify settings for Veeam Agent for Microsoft Windows:

1. At the Options step of the wizard, click Advanced.
2. If you want to limit bandwidth consumption for Veeam Agent backup jobs, on the Agent for Windows tab, in the Network section, select the Limit bandwidth consumption to check box. Then specify the maximum speed for transferring backed-up data from the Veeam Agent computer to the target location.
3. By default, backup over metered connections is disabled for Veeam Agent for Microsoft Windows. Veeam Agent automatically detects metered connections and does not perform backup when your computer is on such connection. To enable backup over metered connections, clear the Restrict metered connections usage check box.

|  |
| --- |
| ![Veeam Agent for Microsoft Windows Settings](images/icon_note.webp)NOTE |
| You must specify which connections are metered in Microsoft Windows. To learn more, see [this Microsoft webpage](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq). |

1. If you want to disable backup over VPN connections, select the Restrict VPN connections usage check box. Veeam Agent for Microsoft Windows will automatically detect VPN connections and will not perform backup when the Veeam Agent computer is on such connection.
2. If you want to restrict usage of wireless networks for Veeam Agent running on Microsoft Windows workstations, do the following:

1. Select the Restrict Wi-Fi usage to these networks only check box and click Add.
2. In the Wi-Fi Network window, specify the SSID of the Wi-Fi network over which Veeam Agent will be allowed to perform backup, and click OK.

Veeam Backup & Replication will add the specified network to the list of allowed Wi-Fi networks. Backup over other wireless networks will be disabled for Veeam Agent.

|  |
| --- |
| ![Veeam Agent for Microsoft Windows Settings](images/icon_tip.webp) TIP |
| If you want to restrict usage over any wireless networks, select the Restrict Wi-Fi usage to these networks only check box and do not add any networks to the list. |

1. If you want to throttle Veeam Agent activities during backup, in the Backup I/O control section, make sure that the Throttle agent activity on option is selected. Then select the type of computers on which to throttle Veeam Agent backup activities: Workstations only, Servers only or All hosts.

If you do not want to throttle backup activities for Veeam Agent, select Do not throttle agent.

1. In the Security section, select the Allow file level recovery without administrative account check box. With this option enabled, Veeam Agent computer users who work under accounts that do not have administrative privileges will be able to perform file-level restore on the Veeam Agent computer.

In this case, access rights to files and folders are managed by Veeam Agent computer OS. If user cannot access the folder in the original location, this user cannot browse or restore the content of this folder as well.

To learn more, see [Restoring Files from Backup without Administrator Privileges](appendix_b_restore_file_not_admin.md).

![Veeam Agent for Microsoft Windows Settings](images/protection_group_vaw.webp "Specify Veeam Agent Settings")

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
