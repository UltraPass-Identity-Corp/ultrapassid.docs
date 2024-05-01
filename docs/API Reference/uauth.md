---
layout: default
title: UAuth
nav_order: 3
parent: API Reference
---

# UAuth Integrations
<sub>{% last_modified_at %}</sub>

UAuth is a secure and flexible decentralized identity provider that enables privacy preserving authentication in various systems and applications.

- [**OpenID Connect (OIDC)**](https://openid.net/developers/how-connect-works/) is a standard protocol for identity authentication and authorization. OIDC integration enables you to use UAuth as an identity provider for any system or application; enabling ease of integration of privacy preserving unique identifiers.

OIDC Service Endpoint:

* **auth.ultrapassid.com**

## Authorization Code Flow with PKCE

The Authorization Code Flow with PKCE (Proof Key for Code Exchange) is a secure OAuth 2.0 authentication method that enhances the security of the standard Authorization Code flow. It's particularly designed for applications that can't securely store client secrets, such as native and single-page applications, but can also be used for confidential clients.

Here's a high-level overview:

1. **Client Registration**: The client (application) registers with the authorization server and obtains a client ID.

2. **Code Challenge and Method**: Before making the authorization request, the client generates a code verifier and a code challenge. The code challenge is derived from the code verifier by using a method such as S256 (SHA256).

3. **Authorization Request**: The client directs the resource owner (user) to the authorization server, including the code challenge and the method used to derive it.

4. **Authorization Grant**: If the resource owner consents, the authorization server issues an authorization code to the client.

5. **Token Request**: The client requests an id token (and optionally an access token) from the authorization server's token endpoint by including the authorization code and the code verifier.

6. **Token Response**: The authorization server validates the code verifier against the previously received code challenge. If valid, it responds with an id token and, if requested, an access token.

This flow ensures that even if an authorization code is intercepted, it cannot be exchanged for an id token without the code verifier, which is not exposed in the authorization request. This mitigates the risk of authorization code interception attacks and makes the Authorization Code Flow with PKCE suitable for both public and confidential clients.

### Authentication Flow
![alt text](../../../assets/images/OIDC_AuthorizationCodeFlowPKCE.png "OIDC - Authorization Code Flow with PKCE")

{: .fs-6 .fw-300 }