---
title: "Verifying Passwords"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/password_manager_verify.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Verifying Passwords

In this article

Veeam Backup & Replication allows you to verify encryption passwords created in the Password Manager. You can perform this operation periodically to make sure that you use a correct password.

To do this, perform the following steps:

1. From the main menu, select Credentials & Passwords > Encryption Passwords.
2. Select the password and click Verify.
3. Enter the password and click OK. If the passwords match, the verification is passed.

|  |
| --- |
| Note |
| Verification will be blocked for 5 minutes if there are 15 unsuccessful attempts in one minute. This mechanism reduces the risk of brute force attacks. |

![Verifying Passwords](images/password_manager_verify_pass.webp)

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
