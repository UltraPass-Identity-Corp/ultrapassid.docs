---
layout: default
title: "TrustLink"
nav_order: 2
has_children: true
permalink: /docs/trustlink
last_modified_date: 2024-05-05
---

# UltraPass TrustLink

UltraPass TrustLink is a robust platform that facilitates the exchange of verifiable data. It is engineered with interoperability as a core principle, utilizing global open standards to ensure seamless interactions across different systems.

This documentation provides a foundational understanding of the UltraPass TrustLink verifiable credential platform and its key components.

## Key Terminology

### Verifiable Credentials

Verifiable Credentials are digital attestations that contain claims made by an Issuing Organization about a subject. These credentials are cryptographically secure, tamper-evident, and can be verified by anyone through cyptographic signatures and decentralized identifiers.

### Credential Fields

Credential Fields are the specific pieces of information contained within a verifiable credential. These fields are defined by the Issuance Schema and can include data such as the credential holder's personal data, entitlements, and other relevant information about the subject.

### Schemas

Schemas are structured data definitions that outline the format and content of a verifiable credential. There are two primary types of Schemas:

- **Issuance Schemas**: These are created and published by Issuing Organizations on the TrustLink Marketplace. They define the data structure and content that the issuing organization will include in the credentials they issue.

- **Verification Schemas**: These are utilized by Verifying Organizations to validate the credentials presented to them. Verification Schemas are onboarded by Verifying Organizations to ensure that the credentials they receive comply with the required standards set by the published Issuance Schema.

### TrustLink Marketplace

The TrustLink Marketplace is a credential discovery platform where Issuing and Verifying Organizations interact. Issuing Organizations publish their Issuance Schemas on the marketplace, making them available for Verifying Organizations to onboard. This marketplace serves as a centralized hub for managing and exchanging verifiable credentials.

## Standards Compliance and Interoperability:

### Credential Exchange

TrustLink supports the **OpenID4VC** standard for credential exchange, which is an extension of OpenID Connect tailored for verifiable credential applications. This standard allows for market interoperability with secure credential exchange and ensures adherence to established protocols. The supported credential formats include **JSON-LD**, **JWT**, and **SD-JWT** **W3C Verifiable Credentials** as well as **ISO/IEC 18013-5 mdoc/mDL**.

**OpenID4VC** provides a structured approach to credential issuance and presentation, allowing for a variety of credential formats to be issued and presented. It follows familiar patterns within the OpenID specifications family, ensuring a consistent and reliable framework for digital identity verification.

### Decentralized Identifiers (DIDs)

DIDs are a new type of identifier that enables verifiable, self-sovereign digital identities. DIDs are fully under the control of the DID subject, independent from any centralized registry, identity provider, or certificate authority. DIDs are used in conjunction with verifiable credentials, which allow the holder to present proof of ownership of the credential without revealing any additional information.

The TrustLink verifiable credential platform currently supports several DID methods, including:

- `did:jwk`: This method is a simplified approach to creating a DID. It encodes a JSON Web Key (JWK) using a base64url, which results in a self-contained identifier that doesn't rely on a blockchain or distributed ledger technology. This method is particularly appealing for its straightforwardness and ease of use, making it a practical choice for those seeking to implement decentralized identifiers without the complexity of other methods. This is the default method used for non-production environments and simple use-cases.

- `did:web`: The `did:web` method allows for DIDs to be associated with a domain name, enabling the resolution of DIDs over the web's existing DNS infrastructure. This method leverages the security and infrastructure of the internet to provide a simple, human friendly, and robust means of managing DIDs.

- `did:cheqd`: This method is built on the [Cheqd network](https://github.com/cheqd), a public permissionless blockchain network for self-sovereign identity and verifiable credentials. `did:cheqd` enables users to control their identity data and credentials through a decentralized ledger, ensuring security and privacy. This method can be used where blockchain or distributed ledger technology is required.

  > _It is important to consider the ramifications of committing decentralized identifiers to an immutable ledger. What may not be considered PII today, may become so in the future._

Each of these methods provides a unique approach to creating and managing DIDs, offering flexibility and choice for users of the TrustLink platform. By supporting multiple DID methods, TrustLink ensures interoperability, broad adoption, and the ability to address any use-case in the ecosystem of decentralized identity.

## Integration:

The integration process with TrustLink is designed to be straightforward, enabling organizations to issue and verify credentials efficiently, without the need for complex infrastructure. TrustLink administrators can use the UltraPass Portal for managing TrustLink Schemas and browsing the TrustLink Marketplace.

For more detailed information on integration and usage, please refer to our SDKs or [TrustLink API Reference](https://docs.ultrapassid.com/docs/API%20Reference/TrustLink.html) documentation.

{: .fs-6 .fw-300 }
