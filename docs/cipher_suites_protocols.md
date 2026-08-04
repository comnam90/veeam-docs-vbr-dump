---
title: "Supported Cipher Suites and Protocols"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cipher_suites_protocols.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Supported Cipher Suites and Protocols


Veeam Backup & Replication supports TLS and SSH secure communication protocols.

TLS

Veeam backup infrastructure components support the following TLS versions:

* TLS 1.3 including mutual TLS (mTLS). Veeam Backup & Replication uses this by default.
* TLS 1.2 including mutual TLS (mTLS).

To avoid negotiation problems between Veeam Backup & Replication and a Microsoft Windows server, ensure that both sides of communication support the same cipher suites.

|  |
| --- |
| Note |
| For security reasons, disable outdated protocols TLS 1.0 and 1.1 if they are not needed. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/windows-server/security/tls/tls-registry-settings?tabs=diffie-hellman#tls-dtls-and-ssl-protocol-version-settings). |

Post-Quantum Cryptography (PQC)

Veeam Backup & Replication can use post-quantum cryptography (PQC) to protect the key exchange for network traffic between [Veeam Data Movers](veeam_transport_service.md). The key exchange is based on a hybrid algorithm that combines a classic elliptic-curve algorithm with post-quantum ML-KEM (NIST FIPS 203). Post-quantum algorithms secure the key exchange only; backup data is still encrypted with AES. This protects the exchanged session keys against the harvest-now, decrypt-later threat, when data captured today could be decrypted in the future by quantum computers.

PQC cannot be used if the FIPS-compliant operation mode is enabled, because post-quantum algorithms are not yet FIPS-validated. Note that the backup server on Linux has FIPS-compliant operation mode enabled by default.

SSH

To avoid negotiation problems between Veeam Backup & Replication and a Linux server, the latter should use ciphers, Key Exchange (KEX) algorithms, and MAC algorithms compatible with SSH libraries supported by Veeam Backup & Replication:

SSH

| Algorithms | Supported values |
| Ciphers | Recommended: aes128-ctr, aes192-ctr, aes256-ctr, aes128-gcm@openssh.com, aes256-gcm@openssh.com, chacha20-poly1305@openssh.com  Supported for backward compatibility: 3des-cbc, 3des-ctr, aes128-cbc, aes192-cbc, aes256-cbc, arcfour, arcfour128, arcfour256, blowfish-cbc, blowfish-ctr, cast128-cbc, twofish-cbc, twofish128-cbc, twofish128-ctr, twofish192-cbc, twofish192-ctr, twofish256-cbc, twofish256-ctr |
| KEX algorithms | Recommended: diffie-hellman-group-exchange-sha256, diffie-hellman-group14-sha256, diffie-hellman-group15-sha512, diffie-hellman-group16-sha512, ecdh-sha2-nistp256, ecdh-sha2-nistp384, ecdh-sha2-nistp521, curve25519-sha256, curve25519-sha256@libssh.org  Supported for backward compatibility: diffie-hellman-group1-sha1, diffie-hellman-group14-sha1, diffie-hellman-group-exchange-sha1 |
| MAC algorithms | Recommended: hmac-sha2-256, hmac-sha2-512, hmac-sha2-256-etm@openssh.com, hmac-sha2-512-etm@openssh.com  Supported for backward compatibility: hmac-md5, hmac-md5-96, hmac-sha-256-96, hmac-sha1-96, hmac-sha2-512-96, hmac-ripemd160, hmac-ripemd160@openssh.com, hmac-sha1 |

Ensure that your SSH configuration on the Linux server allows you to use at least one cipher, KEX algorithm, and MAC algorithm from the table above. You can run the following command to verify the list of allowed algorithms:

|  |
| --- |
| sudo sshd -T | grep "\(ciphers\|macs\|kexalgorithms\)" |

Page updated 2026-07-14

