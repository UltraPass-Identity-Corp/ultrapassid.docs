---
layout: default
title: TrustLink
parent: API Reference
nav_order: 2
---

<h1 id="-uauth">TrustLink Issuance</h1>
<sub>{% last_modified_at %}</sub>

<br>

> Create a verifiable credential offer based on a TrustLink Schema containing supplied user data. Returned response can be displayed to an end user with a QR Code or Deeplink.

## GenerateCredential

<a id="opIdGenerateCredential"></a>

> Code samples

```http
POST /trustlink/v1/issueCredential HTTP/1.1

Content-Type: application/json
Accept: application/json

```

`POST /v1/issueCredential`

> Body parameter

```json
"{\"schemaKey\":\"18222c6f-04e9-4296-8690-d4637eab573b\",\"credentialFields\":{\"First Name\":\"John\",\"Last Name\":\"Doe\",\"Date of Birth\":\"01/01/1970\",\"City\":\"New York\",\"State\":\"NY\"}}"
```

<h3 id="generatecredential-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[generateCredentialRequest](#schemageneratecredentialrequest)|true|Generates a new Credential|

> Example responses

> 201 Response

```json
"{\"credential\":{\"openIdCredentialOffer\":\"openid-credential-offer://issuer.ultrapassid.com/?credential_offer=%7B%22credential_issuer%22%3A%22https%3A%2F%2Fissuer.ultrapassid.com%22%2C%22credentials%22%3A%5B%7B%22format%22%3A%22jwt_vc_json%22%2C%22types%22%3A%5B%22VerifiableCredential%22%2C%22UniversityDegreeCredential%22%5D%2C%22credential_definition%22%3A%7B%22%40context%22%3A%5B%22https%3A%2F%2Fwww.w3.org%2F2018%2Fcredentials%2Fv1%22%2C%22https%3A%2F%2Fwww.w3.org%2F2018%2Fcredentials%2Fexamples%2Fv1%22%5D%2C%22types%22%3A%5B%22VerifiableCredential%22%2C%22UniversityDegreeCredential%22%5D%7D%7D%5D%2C%22grants%22%3A%7B%22authorization_code%22%3A%7B%22issuer_state%22%3A%22de11c246-2357-42f0-a791-8dc19f0a4353%22%7D%2C%22urn%3Aietf%3Aparams%3Aoauth%3Agrant-type%3Apre-authorized_code%22%3A%7B%22pre-authorized_code%22%3A%22eyJhbGciOiJFZERTQSJ9.eyJzdWIiOiJkZTExYzI0Ni0yMzU3LTQyZjAtYTc5MS04ZGMxOWYwYTQzNTMiLCJpc3MiOiJodHRwczovL2lzc3Vlci5wb3J0YWwud2FsdC5pZCIsImF1ZCI6IlRPS0VOIn0.eEfCrHBW9-WcKS8BuXh4HjxHF5QeAzrNg0mi2OVsSOHqcLZNuMyWck8ER0WdEQrT4zNptJpRj2fp71KGZvJ3AA%22%2C%22user_pin_required%22%3Afalse%7D%7D%7D\"}}"
```

<h3 id="generatecredential-responses">Responses</h3>

|Status|Meaning|Description|Model|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Credential has been genrated|[generateCredentialResponse](#schemageneratecredentialresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request not valid|string|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
x-upid-organization-key
</aside>

# Models

<h2 id="tocS_credentialDto">credentialDto</h2>

<a id="schemacredentialdto"></a>
<a id="schema_credentialDto"></a>
<a id="tocScredentialdto"></a>
<a id="tocscredentialdto"></a>

```json
{
  "openIdCredentialOffer": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|openIdCredentialOffer|string|false|none|none|

<h2 id="tocS_generateCredentialRequest">generateCredentialRequest</h2>

<a id="schemageneratecredentialrequest"></a>
<a id="schema_generateCredentialRequest"></a>
<a id="tocSgeneratecredentialrequest"></a>
<a id="tocsgeneratecredentialrequest"></a>

```json
"{\"schemaKey\":\"18222c6f-04e9-4296-8690-d4637eab573b\",\"credentialFields\":{\"First Name\":\"John\",\"Last Name\":\"Doe\",\"Date of Birth\":\"01/01/1970\",\"City\":\"New York\",\"State\":\"NY\"}}"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemaKey|string(uuid)|false|none|none|
|credentialFields|object|false|none|none|
|» **additionalProperties**|string|false|none|none|

<h2 id="tocS_generateCredentialResponse">generateCredentialResponse</h2>

<a id="schemageneratecredentialresponse"></a>
<a id="schema_generateCredentialResponse"></a>
<a id="tocSgeneratecredentialresponse"></a>
<a id="tocsgeneratecredentialresponse"></a>

```json
"{\"credential\":{\"openIdCredentialOffer\":\"openid-credential-offer://issuer.ultrapassid.com/?credential_offer=%7B%22credential_issuer%22%3A%22https%3A%2F%2Fissuer.ultrapassid.com%22%2C%22credentials%22%3A%5B%7B%22format%22%3A%22jwt_vc_json%22%2C%22types%22%3A%5B%22VerifiableCredential%22%2C%22UniversityDegreeCredential%22%5D%2C%22credential_definition%22%3A%7B%22%40context%22%3A%5B%22https%3A%2F%2Fwww.w3.org%2F2018%2Fcredentials%2Fv1%22%2C%22https%3A%2F%2Fwww.w3.org%2F2018%2Fcredentials%2Fexamples%2Fv1%22%5D%2C%22types%22%3A%5B%22VerifiableCredential%22%2C%22UniversityDegreeCredential%22%5D%7D%7D%5D%2C%22grants%22%3A%7B%22authorization_code%22%3A%7B%22issuer_state%22%3A%22de11c246-2357-42f0-a791-8dc19f0a4353%22%7D%2C%22urn%3Aietf%3Aparams%3Aoauth%3Agrant-type%3Apre-authorized_code%22%3A%7B%22pre-authorized_code%22%3A%22eyJhbGciOiJFZERTQSJ9.eyJzdWIiOiJkZTExYzI0Ni0yMzU3LTQyZjAtYTc5MS04ZGMxOWYwYTQzNTMiLCJpc3MiOiJodHRwczovL2lzc3Vlci5wb3J0YWwud2FsdC5pZCIsImF1ZCI6IlRPS0VOIn0.eEfCrHBW9-WcKS8BuXh4HjxHF5QeAzrNg0mi2OVsSOHqcLZNuMyWck8ER0WdEQrT4zNptJpRj2fp71KGZvJ3AA%22%2C%22user_pin_required%22%3Afalse%7D%7D%7D\"}}"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|credential|[credentialDto](#schemacredentialdto)|false|none|none|

