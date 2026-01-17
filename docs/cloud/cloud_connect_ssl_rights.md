---
title: "Rights and Permissions to Access TLS Certificates"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_ssl_rights.html"
last_updated: "1/5/2024"
product_version: "13.0.1.1071"
---

# Rights and Permissions to Access TLS Certificates


The Windows account under which the Veeam Cloud Connect Service on the SP Veeam backup server runs must have the following permissions:

1. The Windows account must have access to the private key in the non-interactive mode (without having to enter a password).
2. The Windows account must have access to the TLS certificate store folder where the private key is kept and must have read rights for this folder. To learn more about key directories and files, see [Microsoft documentation](https://docs.microsoft.com/en-us/windows/desktop/SecCNG/key-storage-and-retrieval#key-directories-and-files).

A self-signed TLS certificate generated with Veeam Backup & Replication is placed to the Shared certificate store. The following Windows accounts have access to this certificate:

+ User who created the TLS certificate
+ LocalSystem Windows account
+ Local Administrators group

1. The Windows account must have access to the TLS certificate itself (stored in the registry) and permissions to the registry folders that contain that certificate.

A self-signed TLS certificate generated with Veeam Backup & Replication is placed to Local Machine\Trusted Root and Local Machine\My registry folders. These folders do not contain any private information and all users have access to these folders by default.


