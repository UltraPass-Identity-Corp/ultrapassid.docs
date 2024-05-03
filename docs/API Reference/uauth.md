---
layout: default
title: UAuth
nav_order: 3
parent: API Reference
---

# UAuth Integration
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

## Authorization Code Flow Requests

### Authorization Request
```http
GET /oauth2/v2.0/authorize? HTTP/1.1
client_id={app_registration_client_id}
&response_type=code
&redirect_uri={redirect_uri}
&response_mode=query
&scope=openid
&code_challenge={client_generated_code_challenge}
&code_challenge_method=S256
```

|Parameter|Required|Description|
|---|---|---|
|client_id|true|ClientId of the Registered Application in the UltraPass Portal|
|response_type|true|Must include ```code```|
|redirect_uri|true|A valid redirect_uri configured for the Registered Application in the UltraPass Portal|
|scope|true|Should contain either ```openid``` or can use default scope by specifying the client_id if access_tokens are required|
|code_challenge|true|The ```code_challenge``` is a Base64 URL-encoded SHA256 hash of the ```code_verifier```. The ```code_verifier``` must be stored within your application for later use. For more information on using a ```code_verifier``` and generating a ```code_challenge```, see the [PKCE RFC](https://datatracker.ietf.org/doc/html/rfc7636). 
|code_challenge_method|true|This is the method used to encode the ```code_verifier``` when generating the value for the ```code_challenge``` parameter. This MUST be S256.|
|response_mode|false|Determines how the authoriation code is returned to your application. Accepted values: ```query,form_post,fragment```|

### Token Retrieval
```http
POST /oauth2/v2.0/token? HTTP/1.1
grant_type=authorization_code
&client_id={app_registration_client_id}
&scope=openid
&code={received_authoriation_code}
&redirect_uri={redirect_uri}
&code_verifier={client_generated_code_verifier}

Content-Type: application/x-www-form-urlencoded
```

|Parameter|Required|Description|
|---|---|---|
|grant_type|true|This must be ```authorization_code```|
|client_id|true|ClientId of the Registered Application in the UltraPass Portal|
|scope|true|Should contain either ```openid``` or can use default scope by specifying the client_id if access_tokens are required|
|code|true|The ```code``` previously returned from the ```/authorize``` endpoint.| 
|redirect_uri|true|A valid redirect_uri configured for the Registered Application in the UltraPass Portal|
|code_verifier|true|The ```code_verifier``` used in the previous ```/authorize``` request used to receive an authorization code