---
title: "Step 5. Specify Oracle Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_oracle_settings.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Step 5. Specify Oracle Settings

In this article

At this step of the wizard, specify the location to which you want to publish the database.

* Select Restore to the original location to publish the database to the original location.
* Select Restore to a different location to publish the database to a custom location.

1. In the Oracle home field, specify the Oracle home directory. To locate the Oracle home directory, click Browse and select the folder you want to use.
2. In the Global database name field, specify the global database name as DB\_NAME.DB\_DOMAIN, where:

* DB\_NAME is the database name. Oracle limits the length of the database name to 8 characters. If the database name you specify exceeds this limit, Veeam Explorer for Oracle will automatically shorten the database name, and hence the global database name, during the publishing process.

The value you specify is also used for the unique database name (DB\_UNIQUE\_NAME) of the published database. The unique database name can contain up to 30 characters.

* DB\_DOMAIN is the domain name of the database. It does not count towards any character limits and Veeam Explorer for Oracle does not shorten it during the publishing process.

For example, if you specify the global database name as orcl\_published.tech.local, Veeam Explorer for Oracle will shorten it to orcl\_pub.tech.local. The database name of the published database will be orcl\_pub, while the unique database name of the published database will be orcl\_published.

1. In the Oracle SID field, specify the database system identifier. The Oracle SID field is automatically filled with the value entered in the Global database name field, but you can also assign a different value.

The maximum length of the Oracle SID is 12 characters and it can only contain alphanumeric characters (a-z, A-Z and 0-9).

Once you have selected a target location for the published database, click Publish.

After you complete this step, a new Published databases node appears at the top of the navigation pane in Veeam Explorer for Oracle. Under this node you can find the databases that have been published during the current session.

[![Specifying Oracle Settings](images/publish_veor_5.webp)](images/publish_veor_5.webp "Specifying Oracle Settings")

[For Windows-based Oracle servers] If the account specified in the previous step is not the Oracle home user, you must provide a password to access the target Oracle home. Applicable to Oracle 12c and later versions.

Note that this window will not appear if you are restoring your data as of a specific transaction and entered the Oracle home user password when configuring the staging server. For more information, see [Configuring Staging Oracle Server](veor_staging_server.md#staging_windows).

[![Specifying Oracle Home User Password](images/veor_publish_oracle_home_password.webp)](images/veor_publish_oracle_home_password.webp "Specifying Oracle Home User Password")

Page updated 8/21/2025

Page content applies to build 13.0.1.1071
