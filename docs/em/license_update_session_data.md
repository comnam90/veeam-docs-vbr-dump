---
title: "license_update_session_data"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/license_update_session_data.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

The table below lists the messages that can appear in the automatic license update session log. Similar messages are received as pop-ups after you force the immediate update. Recommendations for users (if applicable) are provided in the Comment field.

| Message | Reason | Comment |
| --- | --- | --- |
| “New license key has been received” | This sequence of messages means automatic license key update procedure has completed successfully. | You can open the License Information dialog in Veeam backup console or the Licensing section in Enterprise Manager to examine the details. |
| “License key type is not supported at the moment” | License key generation failed due to currently unsupported license type. | Currently, automatic update is supported only for licenses associated with Hosting Rental contract type. |
| “License key is invalid” | License signature (identifier) is invalid. | Contact your Veeam sales representative. |
| “Your existing license key is up to date” | License expiration date is more than 7 days from now. | This message could probably been issued due to an accidental attempt to update the license manually. Select to update the license key automatically, and the system will notify you on time. |
| “Your contract has expired, so the license key cannot be updated automatically. Please contact your Veeam sales representative to renew your contract.” | Your contract has expired and needs to be renewed. | Contact your Veeam sales representative for contract renewal. |
| “General license key generation error has occurred” | Web licensing server did not return a new key upon request due to some other reason. | Wait for 24 hours (Veeam will re-try to update the key). Retries will take place for 1 month after key expiration date. |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
