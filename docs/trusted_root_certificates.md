---
title: "Trusted Certificates"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/trusted_root_certificates.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Trusted Certificates

In this article

There are several root and intermediate certificates necessary for the Veeam Backup & Replication to operate correctly. Removal of these certificates from the backup server or infrastructure component may limit the functionality of Veeam Backup & Replication or cause it to fail.

Linux-based backup infrastructure components configured with Veeam Software Appliance or Veeam Infrastructure Appliance have all necessary certificates installed by default.

In most cases, these certificates are already installed on Microsoft Windows and manually configured Linux machines. However, some installations do not contain needed certificate authorities as trusted certificates, or have non-current certificates. This may happen on servers with locked down security settings, or servers with no internet access or if the latest updates are not installed.

Make sure the following certificates are installed on the backup server and components:

* Root certificates:

* <https://www.digicert.com/CACerts/DigiCertAssuredIDRootCA.crt> (DigiCert Assured ID Root CA)
* <https://www.digicert.com/CACerts/DigiCertHighAssuranceEVRootCA.crt> (DigiCert High Assurance EV Root CA)
* <https://support.globalsign.com/ca-certificates/globalsign-root-certificates> (install R1 and R3 certificates)
* <https://files.entrust.com/root-certificates/entrust_g2_ca.cer> (Entrust Root Certification Authority — G2)
* <https://files.entrust.com/root-certificates/CSBR1.cer> (Entrust Code Signing Root Certification Authority — CSBR1)

* Intermediate certificates:

* <https://www.digicert.com/CACerts/DigiCertEVCodeSigningCA-SHA2.crt> (DigiCert EV Code Signing CA — SHA2)
* <https://files.entrust.com/subca-certificates/EVCS2-CSBR1-crosscert.cer>  (Entrust Extended Validation Code Signing CA — EVCS2)

If your backup server does not have internet access, you can download certificate files from another computer.

Page updated 12/2/2025

Page content applies to build 13.0.1.1071
