---
layout: default
title: Schema Management
parent: TrustLink
nav_order: 1
last_modified_date: 2024-05-05
---

# Schema Management

Utilizing the UltraPass portal, users can effortlessly create, manage, and publish schemas that can be discovered by other Organizations in the UltraPass ecosystem, using the TrustLink Marketplace. Follow the tutorials below to create, publish, and onboard Issuance and Verification Schemas.

## Create Issuance Schema

1. **Create New Schema**: On the TrustLink Schemas page, select the 'Create Schema' option.
<br>
![Create Schema](../../../assets/images/CreateSchema.png "Create Schema")

2. **Enter Schema Details**: Fill in the schema information, including the 'Schema Name', 'Credential Type', and 'Expiration Dates'. You can also specify if the credential of this type should be unique per wallet; this only allows a single credential of this type to be present in a user's UAuth wallet.
<br>
![Schema Name](../../../assets/images/SchemaName.png "Schema Name")
3. **Define Credential Fields**: Specify the credential fields by entering 'Field Names', selecting 'Data Type', and marking whether the field is 'Required' for credential issuance.
<br>
![Credential Fields](../../../assets/images/CredentialFields.png "Credential Fields")
4. **Publish to the TrustLink Marketplace**: Once all details are confirmed, publish the issuance schema to the TrustLink Marketplace for discovery by verifying Organizations or save the Schemas as a draft to complete later.
<br>
![Publish Credential](../../../assets/images/PublishCredential.png "Publish Credential")

Once a Schema is published to the TrustLink Marketplace, it can be used by the publishing Organization to issue credentials and be onboarded by a verifying Organization.

## Onboard Verification Schema

1. **Got to TrustLink Marketplace**: On the TrustLink Schemas page with the Verification table selected, select the 'Go to Marketplace' option or navigate to the Marketplace directly.
<br>
![Onboard Schema](../../../assets/images/OnboardSchema.png "Onboard Schema")

2. **Browse the TrustLink Marketplace for Issuers**: Begin by navigating to the TrustLink Marketplace. Here, you can explore a variety of issuers that provide different credential schemas.
<br>
![Select Issuer](../../../assets/images/SelectIssuer.png "Select Issuer")

3. **View Available Published Schemas**: Once you have found an issuer that aligns with your requirements, select them to view their published issuance schemas. This will give you an insight into the types of credentials they offer and the data they make available.
<br>
![View Published Schemas](../../../assets/images/ViewPublishedSchemas.png "View Published Schemas")

4. **Onboard an Issuance Schema for Verification**: After selecting an issuer, browse through the available issuance schemas to find one that suits your verification needs. Once you have made your choice, select the schema to proceed with onboarding.
<br>
![Select Schema](../../../assets/images/SelectSchema.png "Select Schema")

Once a Schema is onboarded from the TrustLink Marketplace, it can be used in Verification requests by verifying Organizations.

Please see the [TrustLink API Reference](https://docs.ultrapassid.com/docs/API%20Reference/TrustLink.html) documentation for information on how to Issue and Verify credentials using Schemas.