---
layout: default
title: TrustLink
nav_order: 1
has_children: true
permalink: /docs/trustlink
last_modified_date: 2024-05-02
---

# UltraPass TrustLink

UltraPass TrustLink is a robust platform that facilitates the exchange of verifiable data. It is engineered with interoperability as a core principle, utilizing global open standards to ensure seamless interactions across different systems.

This documentation provides a foundational understanding of the UltraPass TrustLink verifiable credential platform and its key components.

## Key Terminology

### Verifiable Credentials
Verifiable Credentials are digital attestations that contain claims made by an Issuing Organization about a subject. These credentials are cryptographically secure, tamper-evident, and can be verified by anyone with the necessary Verification Schema.

### Credential Fields
Credential Fields are the specific pieces of information contained within a verifiable credential. These fields are defined by the Issuance Schema and can include data such as the credential holder's personal data, entitlements, and other relevant information about the subject.

### Schemas
Schemas are structured data definitions that outline the format and content of a verifiable credential. There are two primary types of Schemas:

- **Issuance Schemas**: These are created and published by Issuing Organizations on the TrustLink Marketplace. They define the data structure and content that the issuing organization will include in the credentials they issue.

- **Verification Schemas**: These are utilized by Verifying Organizations to validate the credentials presented to them. Verification Schemas are onboarded by Verifying Organizations to ensure that the credentials they receive comply with the required standards set by the published Issuance Schema.

### TrustLink Marketplace
The TrustLink Marketplace is a credential discovery platform where Issuing and Verifying Organizations interact. Issuing Organizations publish their Issuance Schemas on the marketplace, making them available for Verifying Organizations to onboard. This marketplace serves as a centralized hub for managing and exchanging verifiable credentials.

## Standards Compliance and Interoperability:

TrustLink supports the **OpenID4VC** standard for credential exchange, which is an extension of OpenID Connect tailored for verifiable credential applications. This standard allows for market interoperability with secure credential exchange and ensures adherence to established protocols. The supported credential formats include **JSON-LD**, **JWT**, and **SD-JWT** **W3C Verifiable Credentials** as well as **ISO/IEC 18013-5 mdoc/mDL**.

**OpenID4VC** provides a structured approach to credential issuance and presentation, allowing for a variety of credential formats to be issued and presented. It follows familiar patterns within the OpenID specifications family, ensuring a consistent and reliable framework for digital identity verification.

## Integration:

The integration process with TrustLink is designed to be straightforward, enabling organizations to issue and verify credentials efficiently, without the need for complex infrastructure. TrustLink administrators can use the UltraPass Portal for managing TrustLink Schemas and browsing the TrustLink Marketplace.

For more detailed information on integration and usage, please refer to our SDKs or [TrustLink API Reference]("https://docs.ultrapassid.com/docs/API%20Reference/TrustLink.html) documentation.

{: .fs-6 .fw-300 }