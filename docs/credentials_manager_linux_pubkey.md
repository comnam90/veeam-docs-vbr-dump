---
title: "SSH Private Keys"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/credentials_manager_linux_pubkey.html"
last_updated: "1/8/2026"
product_version: "13.0.1.1071"
---

# SSH Private Keys

In this article

You can log on to a Linux server or VM running Linux OS using the Identity/Pubkey authentication method. The Identity/Pubkey authentication method helps protect against malicious applications like keyloggers, strengthens the security level and simplifies launch of automated tasks.

To use the Identity/Pubkey authentication method, you must generate a pair of keys — a public key and private key:

* Public key is stored on Linux servers to which you plan to connect from the backup server. The key is kept in a special authorized\_keys file containing a list of public keys.
* Private key is stored on the client machine — backup server. The private key is protected with a passphrase. Even if the private key is intercepted, the eavesdropper will have to provide the passphrase to unlock the key and use it.

For authentication on a Linux server, the client must prove that it has the private key matching the public key stored on the Linux server. To do this, the client generates a cryptogram using the private key and passes this cryptogram to the Linux server. If the client uses the "correct" private key for the cryptogram, the Linux server can decrypt the cryptogram with a matching public key.

Veeam Backup & Replication has the following limitations for the Identity/Pubkey authentication method:

* Veeam Backup & Replication does not support keys that are stored as binary data, for example, in a file of DER format.
* Veeam Backup & Replication supports only keys whose passphrase is encrypted with algorithms supported by PuTTY:

* AES (Rijndael): 128-bit, 192-bit and 256-bit CBC or CTR (SSH-2 only)
* Blowfish: 128-bit CBC
* Triple-DES: 168-bit CBC

|  |
| --- |
| Tip |
| Veeam Backup & Replication 12 supports PPK file versions 2 and 3. |

* Passphrases generated in PuTTY must only contain ASCII characters. Unicode characters can create decoding issues in Veeam Backup & Replication.

Veeam Backup & Replication supports the following key algorithms: RSA, ECDSA, EdDSA (ED25519). For these algorithms you can use the following key formats:

| Key Formats | Key Algorithms | | |
| --- | --- | --- | --- |
| RSA | ECDSA | EdDSA (ED25519) |
| PEM | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/no.webp) |
| private | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/yes.webp) |
| private-openssh | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/no.webp) |
| sshcom | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/no.webp) | ![SSH Private Keys)](images/no.webp) |
| PKCS8 | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/no.webp) |
| RDC4716 (private-openssh-new) | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/yes.webp) | ![SSH Private Keys)](images/yes.webp) |

|  |
| --- |
| Important |
| If you use VMware VIX/vSphere Web Services, Veeam Backup & Replication does not support usage of public keys for guest processing on Linux guest servers. |

You can create a new credentials record using the Identity/Pubkey authentication method in one of the following ways:

* [Creating an SSH private key using the Veeam Backup & Replication console](credentials_manager_linux_pubkey_console.md)
* [Creating an SSH private key using the Veeam Backup & Replication web UI](credentials_manager_linux_pubkey_web.md)

Page updated 1/8/2026

Page content applies to build 13.0.1.1071
