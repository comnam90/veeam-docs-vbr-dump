---
title: "Archive Tier Data Transfer"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archive_data_transfer.html"
last_updated: "9/23/2024"
product_version: "13.0.1.1071"
---

# Archive Tier Data Transfer

In this article

You can move outdated backup files from the capacity tier or performance tier to the archive tier. After that, the transported files are deleted from the capacity tier or performance tier. They can stay in the performance tier or be deleted from there depending on the data transfer policy of the scale-out backup repository:

* In case the copy policy is selected, the original file stays in the performance tier. The copied file is copied from the performance tier to the capacity tier. After the archive job runs, it is moved from the capacity tier to the archive tier.
* In case the move policy is selected, the original file is moved from the performance tier to the capacity tier. After the archive job session, the files are moved from the capacity tier to archive tier.
* In case you transfer data from the performance tier to the archive tier, the original file is moved from the performance tier to archive tier.

Page updated 9/23/2024

Page content applies to build 13.0.1.1071
