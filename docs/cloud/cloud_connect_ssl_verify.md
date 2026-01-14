---
title: "cloud_connect_ssl_verify"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_ssl_verify.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

When the tenant adds a SP to the Veeam Backup & Replication console, Veeam Backup & Replication retrieves the TLS certificate with a public key from the SP Veeam backup server and saves it to the database with which tenant Veeam backup server communicates.

To make sure that the obtained TLS certificate is really the TLS certificate used by the SP, tenants can verify the TLS certificate with a thumbprint. Verification with the thumbprint helps tenants protect against the “man-in-the middle” attack when the eavesdropper provides a false TLS certificate to tenants and makes tenants believe that they communicate directly with the SP.

To enable thumbprint verification, the SP must pass the TLS certificate thumbprint to the tenant over a secure channel, for example, by email. When the tenant adds the SP, Veeam Backup & Replication offers the tenant to enter the TLS certificate thumbprint to verify if this TLS certificate is the original SP certificate.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
