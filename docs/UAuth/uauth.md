---
layout: default
title: UAuth
nav_order: 2
has_children: true
permalink: /docs/uauth
last_modified_date: 2024-05-03
---
# UltraPass UAuth

## Overview
UltraPass UAuth is a decentralized, privacy-preserving identity provider that utilizes a user's encrypted biometrics to generate hashed unique identifiers. This innovative approach ensures that biometric data remains solely on the user's device, protected by full homomorphic encryption.

## How It Works
1. **Facial Biometrics**: Offered through an OIDC authentication flow, users scan their face using a web or mobile camera instead of entering a username and password. Their biometrics are captured quickly and stored in local storage on device.
2. **Local Encryption**: Users' biometric data is encrypted locally using full homomorphic encryption. This process ensures that only encrypted data leaves the device. Operations are done against the encrypted biometric profile.
3. **Unique Identifier**: UAuth generates a unique identifier from the encrypted biometric profile and all subsequent logins compare encrypted profiles in order to uniquely identify individuals.
4. **Hashing per Organization**: This identifier is then used to create a unique hash for each organization that uses UAuth to authenticate users. Hashing in this manner provides privacy preserving reusuable identity and tracking resilient logins based on user biometrics.
5. **JWT id_token**: The unique hashed identifier is encapsulated within a signed JWT id_token, which is returned to the relying party application; conforming to standards for the OIDC Authorization Code Flow with PKCE.
6. **Verifiable Credentials**: User data can additionally be presented as verifiable credentials, using TrustLink, enhancing security, privacy, and data ownership.

## Privacy and Security
- **No User Data**: UltraPass does not store or maintain any user information. Data is stored in the user's digital wallet; either on device or, if consented, in the UAuth Web Wallet. Your data is your own.
- **Reusable Identity**: UAuth creates a reusable identity based on facial biometrics, preserving user privacy across multiple platforms, applications, and organizations.

## UAuth Digital Wallet

## Overview
UltraPass UAuth also provides an open standards based digital wallet designed for the secure storage, management, and sharing of verifiable credentials free to end user credential holders with support for shared business-based wallets. It offers two distinct solutions: a web-based wallet and a mobile application.

### Web-Based Wallet
The UAuth Wallet web application is a custodial wallet service. Users can trust UltraPass to maintain the integrity and confidentiality of their credential data in exchange for additional convenience. This platform allows for:

- Secure cloud credential storage
- Web based credential management
- Ease of use with no device dependency
- Robust recovery options and storage resiliency

### Mobile Wallet Application
The UAuth Wallet mobile app provides a highly secure non-custodial solution where users remain in possession of their personal data, storing credential data directly on the user's device. It also features additional passwordless authenticator functionality:

- Remain in full control of your data with secure local credential storage leveraging native device encryption
- Limited backup and recovery options requiring multiple device registrations
- MFA Options:
    - Mobile push notifications with number matching
    - Passkey technology integration for passwordless authentication
    - TOTP (Time-based One-Time Password) support for secure authentication

## Security Features
UltraPass UAuth prioritizes security with features such as:

- End-to-end encryption for data protection
- Biometric authentication and proof of personhood for enhanced security
- Robust logging and monitoring

## UAuth Authorization
UAuth supports system entitlements and authorization through verifiable credentials. Control roles and system access by verifying cryptographic signatures on issued permissions during the authentication process.

>Issue UAuth Authorization credentials using TrustLink

Authorization Schema:
```js
{
    "uauthId": guid,
    "roleName": string,
    "roleId": guid,
    "scope": string,
    "enabled": boolean,
    "extensions": object
}
```



{: .fs-6 .fw-300 }