---
layout: default
title: UAuth
nav_order: 1
has_children: true
parent: API Reference
permalink: /docs/api-reference/uauth
---

# UAuth Integrations
<sub>{% last_modified_at %}</sub>

<br>

UAuth is a secure and flexible decentralized identity provider that enables privacy preserving authentication in various systems and applications. UAuth supports two different types of integrations: standards based OIDC and RESTful API.

- **OIDC** stands for OpenID Connect, which is a standard protocol for identity verification and authorization. OIDC integration enables you to use UAuth as an identity provider for any system or application that supports OIDC.
- **API** integration allows you to use UAuth's proprietary API for systems that do not have OIDC support but have the capability to call a RESTful web service. API integration requires more support and development, but provides a more flexible integration; allowing modern authentication flows to be consumed from legacy applications.

## UAuth Authorization

> UAuth supports system entitlements and authorization through verifiable credentials. Control roles and system access by verifying cryptographic signatures on issued permissions during the authentication process.

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

UAuth provides comprehensive technical documentation for both types of integrations, as well as sample code and tutorials to help you get started.

{: .fs-6 .fw-300 }