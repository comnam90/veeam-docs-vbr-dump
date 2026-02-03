---
title: "Automating Installation with Initial Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_linux_silent_deploy_configure.html"
last_updated: "2/3/2026"
product_version: "13.0.1.1071"
---

# Automating Installation with Initial Configuration


You can modify the Veeam Software Appliance ISO file to allow unattended installation and configuration. This allows you to automatically deploy Veeam Software Appliance with preconfigured users, passwords, multi-factor authentication codes, and other settings.

|  |
| --- |
| Important |
| Installing additional Linux packages, third-party applications, or changing OS settings (other than those that can be controlled by the Veeam Host Management Console) on Veeam Appliances is not supported. Veeam Customer Support cannot provide technical support for appliances with unsupported modifications due to their unpredictable impact on the  security, stability, and performance of the appliance. For more information, see [this KB article.](https://www.veeam.com/kb4772) |

Required Edits

To automate the installation and configuration of Veeam Software Appliance, do the following:

1. Download the latest version of the ISO file from the [Product Downloads](https://my.veeam.com/my-products) section of your Veeam account.
2. Unpack the ISO file.
3. Make the following changes to the %path\_to\_unpacked\_ISO\_folder%\EFI\BOOT\grub.cfg file to automate the installation process:

1. To set the default menu entry, change the set default parameter to "Veeam Backup & Replication v13.0>Install - fresh install, wipes everything (including local backups)".
2. To set a GRUB menu timeout, change the set timeout parameter to any positive value.
3. To set all questions to be answered automatically, add inst.assumeyes to the end of the install menu entry LABEL=VeeamSA:/vbr-ks.cfg quiet.

|  |
| --- |
| Note |
| You can automate additional options in the grub.cfg file. To do this, add inst.assumeyes to the end of the appropriate lines. |

1. Save the changes.

1. Make the following changes to the vbr-ks.cfg file to automate the configuration process:

|  |
| --- |
| Important |
| The changes must be added between %post and # post end. |

1. To disable the initialization wizard, add the following line right after log "Veeam post install commands":

|  |
| --- |
| touch /etc/veeam/cockpit\_auto\_test\_disable\_init |

1. To create a configuration file that contains answers for the initialization wizard, add the following code with your specified answers:

|  |
| --- |
| cat << EOF >> /etc/veeam/vbr\_init.cfg  veeamadmin.password=Ex@mp13C0mpl3xP@ssw0rd  veeamadmin.mfaSecretKey=JVDECICTMVRXEZLU  veeamadmin.isMfaEnabled=false  veeamso.password=Ex@mp13C0mpl3xP@ssw0rd2  veeamso.mfaSecretKey=JVDECICTMVRXEZLU  veeamso.isMfaEnabled=true  veeamso.recoveryToken={8\*}-{4\*}-{4\*}-{4\*}-{12\*}  veeamso.isEnabled=true  ntp.servers=myntp01.example.local  ntp.runSync=true  vbr\_control.runInitIso=true  vbr\_control.runStart=true  EOF |

|  |
| --- |
| Note |
| Consider the following when specifying your answers:   * The passwords for the veeamadmin and veeamso account must meet the following requirements:  * 15 characters minimum. * 1 upper case character. * 1 lower case character. * 1 numeric character. * 1 special character. * No more than 3 characters of the same class in a row. For example, you cannot use more than 3 lowercase or 3 numerical characters in sequence.  * The passwords for the veeamadmin and veeamso accounts must be different. * To avoid timing issues with multifactor authentication, it is recommended to set ntp.runSync=true. * The multifactor authentication secret key must be specified as a 16 digit, Base32-encoded string. * The recovery token must be specified using hexadecimal values — 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F. Note that you can generate an appropriate string with the New-Guid cmdlet in Microsoft PowerShell.   If your specified answers do not meet these requirements, the configuration process will fail. To troubleshoot errors, you can use the [Live OS ISO](https://www.veeam.com/kb4761) to view the /var/log/VeeamBackup/veeam\_hostmanager/veeamhostmanager.log file and the system logs files in the /var/log/anaconda directory. |

1. To create a script that will complete the configuration process using the answer file, add the following code:

|  |
| --- |
| set -e  cat << EOF >> /etc/veeam/veeam-init.sh  #!/bin/bash  set -eE -u -o pipefail  /opt/veeam/hostmanager/veeamhostmanager --apply\_init\_config /etc/veeam/vbr\_init.cfg  systemctl disable veeam-init  EOF  chmod +x /etc/veeam/veeam-init.sh |

1. Add a systemd service definition and enable the service to run the script once after the first boot:

|  |
| --- |
| cat << EOF >> /etc/systemd/system/veeam-init.service  [Unit]  Description=One-shot daemon to run /opt/veeam/hostmanager/veeamhostmanager at next boot  [Service]  Type=oneshot  ExecStart=/etc/veeam/veeam-init.sh  RemainAfterExit=no  [Install]  WantedBy=multi-user.target  EOF  systemctl enable veeam-init.service |

1. Repack the ISO.
2. Mount the ISO file to the machine where you plan to install Veeam Software Appliance, or burn the ISO file to a flash drive or other removable storage device. If you plan to install Veeam Software Appliance on a virtual machine, use the built-in tools of the virtualization management software to mount the ISO file.

|  |
| --- |
| Note |
| To create a bootable USB stick, it is recommended that you use [Rufus](https://rufus.ie/en/) with the default settings. Note that you need to select Write in DD Image mode option when prompted. |

1. Boot the machine and wait for the installation and configuration processes to finish. When the machine is ready to use, the Veeam Host Management console will be displayed.

Optional Edits

You can also set the hostname and IP address, but this is optional. To do this, edit the vbr-ks.cfg. file as described in the following sections.

Setting Hostname

To set a specific hostname, edit the hostname parameter in the network command:

|  |
| --- |
| network --bootproto=dhcp --nodns --hostname=examplehostname |

|  |
| --- |
| Note |
| If you want to add the machine to a Microsoft Windows domain, the hostname cannot contain more than 15 characters. |

Setting Static IP Address

To set a static IP address, edit the bootproto parameter and add the ip, netmask, nameserver, and gateway parameters:

|  |
| --- |
| network --bootproto=static --ip=192.0.2.1 --netmask=255.255.255.0 --gateway=192.0.2.254 --nameserver=192.168.2.1,192.168.3.1 --hostname=vbr-MACH\_HASH |


