---
title: "Kerberos Authentication (Storage Systems)"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_limitations_kerberos.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Kerberos Authentication (Storage Systems)

In this article

This section lists requirements, limitations and peculiarities in work of storage systems that use Kerberos authentication.

General Requirements and Limitations

For management connection:

* Kerberos authentication is supported for the following storage systems: Dell Unity (XT), HPE 3PAR StoreServ, HPE Primera, HPE Alletra 9000, HPE Alletra Storage MP B10000, HPE Nimble, HPE Alletra 6000, HPE Alletra 5000, Pure Storage FlashArray, INFINIDAT InfiniBox F Series, Dell SC Series, Dell PowerStore, Dell PowerMax, Hitachi VSP/VSP One Block, NetApp ONTAP, Lenovo ThinkSystem DM/DG Series, NetApp Element, Tintri IntelliFlash.
* Storage systems that use SSH are not supported.

[For VMware integration] For data connections, that is, used during backup and restore:

* Storage systems with NFS 4.1 connectivity are supported: NetApp ONTAP, Dell Unity (XT), Tintri.
* The following Kerberos protocols are supported: krb5, krb5i and krb5p.

User Name Formats

When adding storage systems that use Kerberos, specify user names in the following formats:

* Dell PowerStore: domain\username, username@domain
* Dell SC Series: username, domain\username, username@domain
* Dell Unity (XT): username@domain
* Hitachi VSP/VSP One Block: username
* HPE 3PAR StoreServ, HPE Primera, HPE Alletra 9000, HPE Alletra Storage MP B10000: username
* HPE Nimble, HPE Alletra 6000, HPE Alletra 5000: username, domain\username, username@domain
* INFINIDAT InfiniBox F Series: username
* NetApp Element: username
* NetApp ONTAP, Lenovo ThinkSystem DM/DG Series: domain\username
* Pure Storage FlashArray: username
* Tintri IntelliFlash: username, domain\username, username@domain

Backup and Rescan (VMware integration)

Which protocol Veeam Backup & Replication tries to use during backup and storage rescan depends on the type of the used backup proxy.

* If a Microsoft Windows-based proxy is used, Veeam Backup & Replication first tries to connect without Kerberos at first. If the connection fails, Veeam Backup & Replication tries to connect using Kerberos protocols in the following order: krb5p, krb5i, krb5.

You can change the order by setting the NFSKerberosEncryptionLevel value in the /etc/veeam/veeam\_backup\_and\_replication.conf configuration file on the Linux-based backup server or with the HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication\NFSKerberosEncryptionLevel {DWORD} registry value on the Microsoft Windows-based backup server.

The values can be the following:

* 0 — non-Kerberos -> krb5p -> krb5i -> krb5 (default value)
* 1 — krb5 -> non-Kerberos -> krb5p -> krb5i
* 2 — krb5i -> non-Kerberos -> krb5p -> krb5
* 3 — krb5p -> non-Kerberos -> krb5i -> krb5

* If a Linux-based proxy is used, the used protocol depends on how the mount command is implemented in the used Linux distributive.

You can specify the order by setting the SanNfsLinuxMountOptions value in the /etc/veeam/veeam\_backup\_and\_replication.conf configuration file on the Linux-based backup server or with the HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication\SanNfsLinuxMountOptions {REG\_MULTI\_SZ} registry value on the Microsoft Windows-based backup server.

This value allows you to override Linux-based proxy mount settings for backup from storage snapshots and storage NFS rescan. You need to specify NFS share path, semicolon and the list of mount parameters separated by commas. In the NFS share path, you can use wildcards: \* to represent any number of letters, and ? for a single letter. For example, 172.24.24.\*;rw,soft,vers=4.1,timeo=300,retrans=10,sec=krb5.

Restore (VMware integration)

During restore from a storage snapshot, Veeam Backup & Replication creates an NFS datastore using non-Kerberos protocol. If the connection fails, Veeam Backup & Replication tries to use Kerberos protocols in the following order: krb5, krb5i.

You can specify the protocol by setting the SanRestoreNfsKerberosEncryptionLevel value in the /etc/veeam/veeam\_backup\_and\_replication.conf configuration file on the Linux-based backup server or with the HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication\SanRestoreNfsKerberosEncryptionLevel (DWORD} registry value on the Microsoft Windows-based backup server.

The values can be the following:

* 0 — non-Kerberos -> krb5 -> krb5i (default value)
* 1 — non-Kerberos
* 2 — krb5
* 3 — krb5i

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
