---
title: "Linux File Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/multios_restore_before_you_begin.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Linux File Recovery

In this article

This section lists considerations and limitations that apply to recovery from Linux workloads.

Infrastructure Components

* [For source and target workload] Veeam Backup & Replication uses the ICMP ping command to define whether a workload is available over the network. If the workload must be available over the network, check that ICMP protocol is enabled on the workload.
* Recovery from Linux workloads is possible only when using a Linux-based mount server (helper appliance, Linux mount server or Linux helper host).
* The following applies if you recover VMware vSphere VMs:

* Veeam Backup & Replication must have access over the network to the guest OS of the target workload or direct access to the vCenter or ESXi host where the target workload resides to deploy a coordination process. The coordination process performs a number of administrative actions on the target workload guest OS, for example, it collects information about mount points.

* The mount server, helper host and helper appliance must have access over the network to a VM whose files you recover or direct access to the vCenter server or ESXi host where the VM resides. If a network connection cannot be established, the mount server connects to the VM over VIX API/vSphere Web Services. In this case, you must use a root account for the target workload and check that /tmp directory on the target workload is mounted with the exec option. Otherwise, the recovery process will fail.

If you use the FQDN of the ESXi host in the [helper appliance configuration window](multios_restore_proxy_vm.md), the helper appliance must be able to resolve the FQDN of the ESXi host.

[For Linux-based backup server] If your DHCP does not provide the DNS configuration, assign the DNS server address manually by editing the /etc/veeam/veeam\_backup\_and\_replication.conf file. Add the DnsServersList variable in the root section and set it to the required value. If you want to specify multiple addresses, separate them using a comma. After you specify the value, restart the recovery process.

[For Microsoft Windows-based backup server] If your DHCP does not provide the DNS configuration, assign the DNS server address manually using the [HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication\DnsServersList]registry value. This value accepts data of the REG\_SZ type, for example, 10.11.12.13. If you want to specify multiple addresses, separate them using a semicolon. After you specify the registry value, restart the recovery process.

* [For helper appliance] If you recover data from a CDP replica, the helper appliance must be deployed on an ESXi host or cluster where the I/O filter is installed.
* You can recover from Novell Storage Services (NSS) file system if you use FUSE or a helper appliance. When using FUSE, the helper host must differ from the backed-up VM. When using the helper appliance, you can perform recovery only in the IPv4 environment.

* The following applies if you recover Microsoft Hyper-V VMs:

* Veeam Backup & Replication must have access to the guest OS of the target workload to deploy a coordination process. The coordination process performs a number of administrative actions on the target workload guest OS, for example, it collects information about mount points.

* The mount server, helper host and helper appliance, must have access over the network to a VM whose files you recover and to Hyper-V host where the VM resides.

Source for Data Recovery

* You can recover files whose names are written in all locales in the UTF-8 encoding. If the encoding is other than UTF-8, you can recover only files whose names are written in the English locale.

* Recovery from workloads with data deduplication enabled is not supported.

* [For backups of BSD, macOS and Solaris VMs] You cannot recover files directly to the original location. Use the Copy to option instead.

* [For backups of Linux workloads] You can recover files from basic disks, Linux LVM (Logical Volume Manager) and ZFS pools. Encrypted, RAID1 and mirrored LVM volumes are not supported.
* [For backups of Linux workloads] RAID mounts and recoveries are not supported.

* [If you recover from backups with guest file system indexing disabled] To properly show the file system tree in the Veeam Backup browser, check that the /etc/fstab file lists disk UUIDs or labels. Disks listed using device names are shown outside the file system tree as separate disks. For more information on guest file system indexing, see Guest OS File Indexing in [vSphere backup jobs](backup_job_vss_indexing_vm.md) or in [Hyper-V backup jobs](backup_job_vss_indexing_hv.md).

Target for Data Recovery

* The following applies if guest processing components are not installed on the target workload:

* Make sure that the /tmp directory on the target workload is mounted with the exec option. Otherwise, you will get a permission denied error.
* If you recover files using the account for which only the [Elevate account privileges automatically](credentials_manager_linux_console.md) check box is selected, the /home/<username> directory also must be mounted with the exec option.

* [For [recovery to a new location](guest_restore_save.md)] You can recover items only to Linux-based workloads. BSD, macOS and Solaris VMs are not supported.

* [For recovery to a new location] If you want to recover files over the network, make sure that the SSH daemon is configured and the SCP utility is available on the target workload.
* [For recovery to a new location] Veeam Backup & Replication can recover ACL for recovered guest OS files. To let Veeam Backup & Replication detect the target Linux system architecture and kernel version, the following utilities must be present in the minimal configuration of the system: arch and uname.
* For backups created by Veeam Agents, you can use the [Restore to](guest_restore_save.md) (recovery to a new location) command only if the target computer is available over the network. This applies to backups created by Veeam Agent for Linux, Veeam Agent for IBM AIX or Veeam Agent for Oracle Solaris.

Recovery Finalization

* The following operations are available for recovering from a Linux workload: recovery to original location (Restore), recovery to another location (Restore to), and copy (Copy to), access files over FTP, and access helper appliance logs.
* The following applies to the Copy to operation:

* Only Linux servers can be added ad hoc.
* To restore original permissions and ownership settings, the user account you have specified must have privileges to change the owner on the selected server or shared folder.
* If you recover files to the Linux-based backup server, only the /var/lib/veeam directory is accessible for browsing and can be used as the destination for the copy operation.

Linux Firewalls in Linux Helper Host and Target for Data Recovery

To use a Linux helper host as the mount server or to recover files to a new location on another Linux workload, consider the following.

Veeam Backup & Replication automatically opens ports used for the recovery process on the mount server and on the target Linux workload. Generally, Veeam Backup & Replication automatically opens ports for the most popular firewalls (iptables, ufw, firewall-cmd). However, if for some reason the ports are not opened, you can open them manually. You can also specify these ports at the [Access](linux_server_ssh.md) step of the New Linux Server wizard. Note that ports are opened dynamically: if 10 concurrent jobs are running, Veeam Backup & Replication opens ports 2500-2509.

If you use the firewalld tool, you can configure firewall rules to open ports only in the necessary zones. By default, Veeam Backup & Replication opens ports in all active firewalld zones. If your firewall is configured for different zones, and you want to minimize security holes, you can configure Veeam Backup & Replication to open the ports only for certain zones. To do this, perform the following:

1. On the Linux helper host or target Linux server, create the /etc/VeeamNetConfig file and define the following parameter:

|  |
| --- |
| FirewalldZones=zone\_name\_1, zone\_name\_2 |

where zone\_name\_1, zone\_name\_2 is a list of zone names where the ports must be open. Veeam Backup & Replication will skip the zones that are not in this list.

1. [Only for Linux helper host] If you select a Linux server that is already added to the Veeam Backup & Replication infrastructure, you should also add required zones to the /opt/veeam/transport/VeeamTransportConfig file.

|  |
| --- |
| FirewalldZones=zone\_name\_1, zone\_name\_2 |

|  |
| --- |
| Note |
| Veeam Backup & Replication opens the port 2500 in all zones even if you have specified the required zones in configuration files. |

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
