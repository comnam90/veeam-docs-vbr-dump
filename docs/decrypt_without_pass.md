---
title: "Decrypting Backups With Enterprise Manager Keys"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/decrypt_without_pass.html"
last_updated: "10/18/2024"
product_version: "13.0.1.1071"
---

# Decrypting Backups With Enterprise Manager Keys


To decrypt backup files with Enterprise Manager keys, you need to issue a request to Veeam Backup Enterprise Manager using the following wizards:

* The Encryption Key Restore wizard on the backup server.
* The Password Recovery wizard on the Veeam Backup Enterprise Manager server.

|  |
| --- |
| Note |
| To generate a request for data restore from a backup server, Veeam Backup & Replication uses the RSA algorithm with a 2048-bit key length. For more information, see [RSA Cryptography Specifications](https://tools.ietf.org/html/rfc8017). |

To complete the operation, perform the following steps:

1. [Create a request for key restore](restore_without_pass_request.md).
2. [Process the request in Veeam Backup Enterprise Manager](restore_without_key_process.md).
3. [Complete the key restore process](restore_without_pass_complete.md).


