---
layout: default
title: Schema Management
parent: TrustLink
nav_order: 1
last_modified_date: 2024-05-02
---

# Schema Management

Utilizing the UltraPass portal, users can effortlessly create, manage, and publish schemas that can be discovered by other Organizations in the UltraPass ecosystem, using the TrustLink Marketplace. Follow the tutorials below to create, publish, and onboard Issuance and Verification Schemas.

## Create Issuance Schema
1. **Create New Schema**: On the TrustLink Schemas page, select the 'Create Schema' option.
<br>
![alt text](../../../assets/images/CreateSchema.png "Create Schema")
2. **Enter Schema Details**: Fill in the schema information, including the 'Schema Name', 'Credential Type', and 'Expiration Dates'. You can also specify if the credential of this type should be unique per wallet; this only allows a single credential of this type to be present in a user's UAuth wallet.
<br>
![alt text](../../../assets/images/SchemaName.png "Schema Name")
![alt text](../../../assets/images/CredentialType.png "Credential Type")
![alt text](../../../assets/images/ExpirationDate.png "Expiration Date")
3. **Define Credential Fields**: Specify the credential fields by entering 'Field Names', selecting 'Data Type', and marking whether the field is 'Required' for credential issuance.
4. **Publish to the TrustLink Marketplace**: Once all details are confirmed, publish the issuance schema to the TrustLink Marketplace for discovery by verifying Organizations or save the Schemas as a draft to complete later.

Once a Schema is published to the TrustLink Marketplace, it can be onboarded by a verifying Organization.