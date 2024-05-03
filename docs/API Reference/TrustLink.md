---
layout: default
title: TrustLink
parent: API Reference
nav_order: 1
last_modified_date:
---

<h1 id="client-api-v1-credentials">TrustLink Credentials</h1>

## GenerateCredentialOfferAsync

<a id="opIdGenerateCredentialOfferAsync"></a>

> Create an open standards verifiable credential offer based on a TrustLink Schema containing supplied user data. Returned response can be displayed to an end user with a QR Code or Deeplink.

> Code samples

```http
POST https://api.ultrapassid.com/client/v1/credentials/issue HTTP/1.1
Host: api.ultrapassid.com
Content-Type: application/json
Accept: application/json

```

`POST /v1/credentials/issue`

Generate Credential Offer from existing Published Schema

> Body parameter

```json
{
  "credentialFields": {
    "property1": "string",
    "property2": "string"
  },
  "schemaKey": "f241d2e0-5a44-4703-974b-ec5012713f0b"
}
```

<h3 id="generatecredentialofferasync-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[GenerateCredentialOfferCommand](#schemageneratecredentialoffercommand)|false|none|

> Example responses

> 201 Response

```json
{
  "expiration_date_time_utc": "2024-05-02T02:31:23.0000000+00:00",
  "open_id_credential_offer": "openid-credential-offer://dev-issuer.ultrapassid.com/?credential_offer_uri=https%3A%2F%2Fdev-issuer.ultrapassid.com%2Fopenid4vc%2FcredentialOffer%3Fid%3D4a63e62f-db3d-4b92-9650-0c7034fc3762"
}
```

> 400 Response

```json
[
  {
    "error_message": "error1",
    "property_name": "property1"
  },
  {
    "error_message": "error2",
    "property_name": "property2"
  },
  {
    "error_message": "error3",
    "property_name": "property3"
  }
]
```

> 424 Response

```json
"Some dependency failed"
```

<h3 id="generatecredentialofferasync-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[CredentialOfferDto](#schemacredentialofferdto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|424|[Failed Dependency](https://tools.ietf.org/html/rfc2518#section-10.5)|Client Error|Inline|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKeyHeader
</aside>

## GenerateVerificationOfferAsync

<a id="opIdGenerateVerificationOfferAsync"></a>

> Create an open standards verifiable credential presentation request based on a TrustLink Schema containing supplied user data. Returned response can be displayed to an end user with a QR Code or Deeplink.

> Code samples

```http
POST https://api.ultrapassid.com/client/v1/credentials/verify HTTP/1.1
Host: api.ultrapassid.com
Content-Type: application/json
Accept: application/json

```

`POST /v1/credentials/verify`

Generate Verification Offer from existing Published Schema

> Body parameter

```json
{
  "schemaKey": "f241d2e0-5a44-4703-974b-ec5012713f0b"
}
```

<h3 id="generateverificationofferasync-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[GenerateVerificationOfferCommand](#schemagenerateverificationoffercommand)|false|none|

> Example responses

> 201 Response

```json
{
  "open_id_verification_offer": "openid4vp://authorize?response_type=vp_token&client_id=&response_mode=direct_post&state=83rvNtvkaf2a&presentation_definition_uri=https%3A%2F%2Fdev-verifier.ultrapassid.com%2Fopenid4vc%2Fpd%2F83rvNtvkaf2a&client_id_scheme=redirect_uri&response_uri=https%3A%2F%2Fdev-verifier.ultrapassid.com%2Fopenid4vc%2Fverify%2F83rvNtvkaf2a"
}
```

> 400 Response

```json
[
  {
    "error_message": "error1",
    "property_name": "property1"
  },
  {
    "error_message": "error2",
    "property_name": "property2"
  },
  {
    "error_message": "error3",
    "property_name": "property3"
  }
]
```

> 424 Response

```json
"Some dependency failed"
```

<h3 id="generateverificationofferasync-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[VerificationDto](#schemaverificationdto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|424|[Failed Dependency](https://tools.ietf.org/html/rfc2518#section-10.5)|Client Error|Inline|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKeyHeader
</aside>

## GetVerificationSessionResultAsync

<a id="opIdGetVerificationSessionResultAsync"></a>

> Retrieve the result of a Verification Request

> Code samples

```http
GET https://api.ultrapassid.com/client/v1/credentials/verify/{sessionId} HTTP/1.1
Host: api.ultrapassid.com
Accept: application/json

```

`GET /v1/credentials/verify/{sessionId}`

Get Credential Verification Session Result

<h3 id="getverificationsessionresultasync-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sessionId|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "credential_subject": {
    "Date of Birth": "1990-01-01",
    "First Name": "John",
    "Last Name": "Doe"
  },
  "policies": {
    "failed": 0,
    "succeeded": 2,
    "total": 2
  },
  "success": true
}
```

> 400 Response

```json
[
  {
    "error_message": "error1",
    "property_name": "property1"
  },
  {
    "error_message": "error2",
    "property_name": "property2"
  },
  {
    "error_message": "error3",
    "property_name": "property3"
  }
]
```

<h3 id="getverificationsessionresultasync-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[OrganizationDto](#schemaorganizationdto)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKeyHeader
</aside>

# Credential Models

<h2 id="tocS_CredentialOfferDto">CredentialOfferDto</h2>
<!-- backwards compatibility -->
<a id="schemacredentialofferdto"></a>
<a id="schema_CredentialOfferDto"></a>
<a id="tocScredentialofferdto"></a>
<a id="tocscredentialofferdto"></a>

```json
{
  "expirationDateTimeUtc": "2019-08-24T14:15:22Z",
  "openIdCredentialOffer": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|expirationDateTimeUtc|string(date-time)|false|none|none|
|openIdCredentialOffer|string¦null|false|none|none|

<h2 id="tocS_CredentialTypeDto">CredentialTypeDto</h2>
<!-- backwards compatibility -->
<a id="schemacredentialtypedto"></a>
<a id="schema_CredentialTypeDto"></a>
<a id="tocScredentialtypedto"></a>
<a id="tocscredentialtypedto"></a>

```json
{
  "key": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|[CredentialTypeKey](#schemacredentialtypekey)|false|none|none|
|name|string¦null|false|none|none|

<h2 id="tocS_CredentialTypeKey">CredentialTypeKey</h2>
<!-- backwards compatibility -->
<a id="schemacredentialtypekey"></a>
<a id="schema_CredentialTypeKey"></a>
<a id="tocScredentialtypekey"></a>
<a id="tocscredentialtypekey"></a>

```json
{
  "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
  "value": "a860a344-d7b2-406e-828e-8d442f23f344"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|guid|string(uuid)|false|none|none|
|value|string(uuid)|false|none|none|

<h2 id="tocS_FieldType">FieldType</h2>
<!-- backwards compatibility -->
<a id="schemafieldtype"></a>
<a id="schema_FieldType"></a>
<a id="tocSfieldtype"></a>
<a id="tocsfieldtype"></a>

```json
0

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(int32)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|0|
|*anonymous*|1|
|*anonymous*|2|
|*anonymous*|4|
|*anonymous*|5|

<h2 id="tocS_GenerateCredentialOfferCommand">GenerateCredentialOfferCommand</h2>
<!-- backwards compatibility -->
<a id="schemageneratecredentialoffercommand"></a>
<a id="schema_GenerateCredentialOfferCommand"></a>
<a id="tocSgeneratecredentialoffercommand"></a>
<a id="tocsgeneratecredentialoffercommand"></a>

```json
{
  "credentialFields": {
    "property1": "string",
    "property2": "string"
  },
  "schemaKey": "f241d2e0-5a44-4703-974b-ec5012713f0b"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|credentialFields|object¦null|false|none|none|
|» **additionalProperties**|string|false|none|none|
|schemaKey|string(uuid)|false|none|none|

<h2 id="tocS_GenerateVerificationOfferCommand">GenerateVerificationOfferCommand</h2>
<!-- backwards compatibility -->
<a id="schemagenerateverificationoffercommand"></a>
<a id="schema_GenerateVerificationOfferCommand"></a>
<a id="tocSgenerateverificationoffercommand"></a>
<a id="tocsgenerateverificationoffercommand"></a>

```json
{
  "schemaKey": "f241d2e0-5a44-4703-974b-ec5012713f0b"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemaKey|string(uuid)|false|none|none|

<h2 id="tocS_IssuanceExpirationPeriod">IssuanceExpirationPeriod</h2>
<!-- backwards compatibility -->
<a id="schemaissuanceexpirationperiod"></a>
<a id="schema_IssuanceExpirationPeriod"></a>
<a id="tocSissuanceexpirationperiod"></a>
<a id="tocsissuanceexpirationperiod"></a>

```json
1

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(int32)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|1|
|*anonymous*|2|
|*anonymous*|3|

<h2 id="tocS_OrganizationDto">OrganizationDto</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationdto"></a>
<a id="schema_OrganizationDto"></a>
<a id="tocSorganizationdto"></a>
<a id="tocsorganizationdto"></a>

```json
{
  "description": "string",
  "domain": "string",
  "imageUrl": "string",
  "key": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "name": "string",
  "websiteUrl": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|description|string¦null|false|none|none|
|domain|string¦null|false|none|none|
|imageUrl|string¦null|false|none|none|
|key|[OrganizationKey](#schemaorganizationkey)|false|none|none|
|name|string¦null|false|none|none|
|websiteUrl|string¦null|false|none|none|

<h2 id="tocS_OrganizationKey">OrganizationKey</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationkey"></a>
<a id="schema_OrganizationKey"></a>
<a id="tocSorganizationkey"></a>
<a id="tocsorganizationkey"></a>

```json
{
  "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
  "value": "a860a344-d7b2-406e-828e-8d442f23f344"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|guid|string(uuid)|false|none|none|
|value|string(uuid)|false|none|none|


<h1 id="client-api-v1-schemaverifiers">Verification Schemas</h1>

> Retrieve available Verification Schemas for the Organization. Verification Schemas can be managed using the Ultrapass Portal.

## GetAllSchemaVerifiersAsync

<a id="opIdGetAllSchemaVerifiersAsync"></a>

> Code samples

```http
GET https://api.ultrapassid.com/client/v1/schema-verifiers HTTP/1.1
Host: api.ultrapassid.com
Accept: application/json

```

`GET /v1/schema-verifiers`

Get all Schema Verifiers

<h3 id="getallschemaverifiersasync-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pageNumber|query|integer(int32)|false|Format - int32. The index of page to return|
|pageSize|query|integer(int32)|false|Format - int32. Number of items returned|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "issuer_key": "23c7007f-7234-4ebc-9a44-1bbd0aa45af1",
      "issuer_name": "UltrapassId Corp",
      "key": "6b8d9d10-25a4-4693-a5ad-10d2f9bd0780",
      "schema_key": "18222c6f-04e9-4296-8690-d4637eab573b",
      "schema_name": "NY Driver's License"
    },
    {
      "issuer_key": "23c7007f-7234-4ebc-9a44-1bbd0aa45af1",
      "issuer_name": "UltrapassId Corp",
      "key": "502b3238-8593-4a4d-8b31-7b6327e16722",
      "schema_key": "502b3238-8593-4a4d-8b31-7b6327e16722",
      "schema_name": "TX Driver's License"
    }
  ],
  "page_number": 1,
  "page_size": 2,
  "total_count": 2
}
```

<h3 id="getallschemaverifiersasync-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[SchemaVerifierDtoPaginatedResponseEntity](#schemaschemaverifierdtopaginatedresponseentity)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKeyHeader
</aside>
<h1 id="client-api-v1-schemas">Published Schemas</h1>

> Retrieve available Published Schemas for the Organization.  Schemas can be managed using the Ultrapass Portal.

## GetAllPublishedSchemasAsync

<a id="opIdGetAllPublishedSchemasAsync"></a>

> Code samples

```http
GET https://api.ultrapassid.com/client/v1/schemas HTTP/1.1
Host: api.ultrapassid.com
Accept: application/json

```

`GET /v1/schemas`


Get all Published Schemas

<h3 id="getallpublishedschemasasync-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pageNumber|query|integer(int32)|false|Format - int32. The index of page to return|
|pageSize|query|integer(int32)|false|Format - int32. Number of items returned|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "credential_type": {
        "key": "b154b8e9-9d55-4962-a1dd-fadc42002e7b",
        "name": "NationalId"
      },
      "fields": [
        {
          "field_type": 0,
          "is_required": true,
          "name": "First Name"
        },
        {
          "field_type": 0,
          "is_required": true,
          "name": "Last Name"
        },
        {
          "field_type": 4,
          "is_required": true,
          "name": "Date of Birth"
        },
        {
          "field_type": 0,
          "is_required": false,
          "name": "City"
        },
        {
          "field_type": 0,
          "is_required": false,
          "name": "State"
        }
      ],
      "is_schema_unique_per_wallet": false,
      "issuance_expiration_date_time_utc": "2025-05-02T12:00:00.0000000+00:00",
      "key": "18222c6f-04e9-4296-8690-d4637eab573b",
      "name": "NY Drivers License",
      "status": 1
    },
    {
      "credential_type": {
        "key": "b154b8e9-9d55-4962-a1dd-fadc42002e7b",
        "name": "NationalId"
      },
      "fields": [
        {
          "field_type": 0,
          "is_required": true,
          "name": "First Name"
        },
        {
          "field_type": 0,
          "is_required": true,
          "name": "Last Name"
        },
        {
          "field_type": 4,
          "is_required": true,
          "name": "Date of Birth"
        },
        {
          "field_type": 0,
          "is_required": false,
          "name": "City"
        },
        {
          "field_type": 0,
          "is_required": false,
          "name": "State"
        }
      ],
      "is_schema_unique_per_wallet": false,
      "issuance_expiration_date_time_utc": "2025-05-02T12:00:00.0000000+00:00",
      "key": "502b3238-8593-4a4d-8b31-7b6327e16722",
      "name": "TX Drivers License",
      "status": 1
    }
  ],
  "page_number": 1,
  "page_size": 2,
  "total_count": 2
}
```

> 400 Response

```json
[
  {
    "error_message": "error1",
    "property_name": "property1"
  },
  {
    "error_message": "error2",
    "property_name": "property2"
  },
  {
    "error_message": "error3",
    "property_name": "property3"
  }
]
```

<h3 id="getallpublishedschemasasync-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[SchemaDtoPaginatedResponseEntity](#schemaschemadtopaginatedresponseentity)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKeyHeader
</aside>

# Schema Models

<h2 id="tocS_OrganizationDto">OrganizationDto</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationdto"></a>
<a id="schema_OrganizationDto"></a>
<a id="tocSorganizationdto"></a>
<a id="tocsorganizationdto"></a>

```json
{
  "description": "string",
  "domain": "string",
  "imageUrl": "string",
  "key": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "name": "string",
  "websiteUrl": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|description|string¦null|false|none|none|
|domain|string¦null|false|none|none|
|imageUrl|string¦null|false|none|none|
|key|[OrganizationKey](#schemaorganizationkey)|false|none|none|
|name|string¦null|false|none|none|
|websiteUrl|string¦null|false|none|none|

<h2 id="tocS_OrganizationKey">OrganizationKey</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationkey"></a>
<a id="schema_OrganizationKey"></a>
<a id="tocSorganizationkey"></a>
<a id="tocsorganizationkey"></a>

```json
{
  "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
  "value": "a860a344-d7b2-406e-828e-8d442f23f344"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|guid|string(uuid)|false|none|none|
|value|string(uuid)|false|none|none|

<h2 id="tocS_SchemaDto">SchemaDto</h2>
<!-- backwards compatibility -->
<a id="schemaschemadto"></a>
<a id="schema_SchemaDto"></a>
<a id="tocSschemadto"></a>
<a id="tocsschemadto"></a>

```json
{
  "credentialType": {
    "key": {
      "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
      "value": "a860a344-d7b2-406e-828e-8d442f23f344"
    },
    "name": "string"
  },
  "fields": [
    {
      "fieldType": 0,
      "isRequired": true,
      "name": "string"
    }
  ],
  "isSchemaUniquePerWallet": true,
  "issuanceExpirationDateTimeUtc": "2019-08-24T14:15:22Z",
  "issuanceExpirationPeriod": 1,
  "issuanceExpirationUnits": 0,
  "key": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "name": "string",
  "status": 1
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|credentialType|[CredentialTypeDto](#schemacredentialtypedto)|false|none|none|
|fields|[[SchemaFieldDto](#schemaschemafielddto)]¦null|false|none|none|
|isSchemaUniquePerWallet|boolean|false|none|none|
|issuanceExpirationDateTimeUtc|string(date-time)¦null|false|none|none|
|issuanceExpirationPeriod|[IssuanceExpirationPeriod](#schemaissuanceexpirationperiod)|false|none|none|
|issuanceExpirationUnits|integer(int32)¦null|false|none|none|
|key|[SchemaKey](#schemaschemakey)|false|none|none|
|name|string¦null|false|none|none|
|status|[SchemaStatus](#schemaschemastatus)|false|none|none|

<h2 id="tocS_SchemaDtoPaginatedResponseEntity">SchemaDtoPaginatedResponseEntity</h2>
<!-- backwards compatibility -->
<a id="schemaschemadtopaginatedresponseentity"></a>
<a id="schema_SchemaDtoPaginatedResponseEntity"></a>
<a id="tocSschemadtopaginatedresponseentity"></a>
<a id="tocsschemadtopaginatedresponseentity"></a>

```json
{
  "data": [
    {
      "credentialType": {
        "key": {
          "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
          "value": "a860a344-d7b2-406e-828e-8d442f23f344"
        },
        "name": "string"
      },
      "fields": [
        {
          "fieldType": 0,
          "isRequired": true,
          "name": "string"
        }
      ],
      "isSchemaUniquePerWallet": true,
      "issuanceExpirationDateTimeUtc": "2019-08-24T14:15:22Z",
      "issuanceExpirationPeriod": 1,
      "issuanceExpirationUnits": 0,
      "key": {
        "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
        "value": "a860a344-d7b2-406e-828e-8d442f23f344"
      },
      "name": "string",
      "status": 1
    }
  ],
  "pageNumber": 0,
  "pageSize": 0,
  "totalCount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[SchemaDto](#schemaschemadto)]¦null|false|none|none|
|pageNumber|integer(int32)|false|none|none|
|pageSize|integer(int32)|false|none|none|
|totalCount|integer(int32)|false|none|none|

<h2 id="tocS_SchemaFieldDto">SchemaFieldDto</h2>
<!-- backwards compatibility -->
<a id="schemaschemafielddto"></a>
<a id="schema_SchemaFieldDto"></a>
<a id="tocSschemafielddto"></a>
<a id="tocsschemafielddto"></a>

```json
{
  "fieldType": 0,
  "isRequired": true,
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fieldType|[FieldType](#schemafieldtype)|false|none|none|
|isRequired|boolean|false|none|none|
|name|string¦null|false|none|none|

<h2 id="tocS_SchemaKey">SchemaKey</h2>
<!-- backwards compatibility -->
<a id="schemaschemakey"></a>
<a id="schema_SchemaKey"></a>
<a id="tocSschemakey"></a>
<a id="tocsschemakey"></a>

```json
{
  "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
  "value": "a860a344-d7b2-406e-828e-8d442f23f344"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|guid|string(uuid)|false|none|none|
|value|string(uuid)|false|none|none|

<h2 id="tocS_SchemaStatus">SchemaStatus</h2>
<!-- backwards compatibility -->
<a id="schemaschemastatus"></a>
<a id="schema_SchemaStatus"></a>
<a id="tocSschemastatus"></a>
<a id="tocsschemastatus"></a>

```json
1

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(int32)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|1|
|*anonymous*|2|
|*anonymous*|3|

<h2 id="tocS_SchemaVerifierDto">SchemaVerifierDto</h2>
<!-- backwards compatibility -->
<a id="schemaschemaverifierdto"></a>
<a id="schema_SchemaVerifierDto"></a>
<a id="tocSschemaverifierdto"></a>OrganizationDto
<a id="tocsschemaverifierdto"></a>

```json
{
  "fields": [
    {
      "fieldType": 0,
      "isRequired": true,
      "name": "string"
    }
  ],
  "issuerKey": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "issuerName": "string",
  "key": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "schemaKey": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "schemaName": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fields|[[SchemaFieldDto](#schemaschemafielddto)]¦null|false|none|none|
|issuerKey|[OrganizationKey](#schemaorganizationkey)|false|none|none|
|issuerName|string¦null|false|none|none|
|key|[SchemaVerifierKey](#schemaschemaverifierkey)|false|none|none|
|schemaKey|[SchemaKey](#schemaschemakey)|false|none|none|
|schemaName|string¦null|false|none|none|

<h2 id="tocS_SchemaVerifierDtoPaginatedResponseEntity">SchemaVerifierDtoPaginatedResponseEntity</h2>
<!-- backwards compatibility -->
<a id="schemaschemaverifierdtopaginatedresponseentity"></a>
<a id="schema_SchemaVerifierDtoPaginatedResponseEntity"></a>
<a id="tocSschemaverifierdtopaginatedresponseentity"></a>
<a id="tocsschemaverifierdtopaginatedresponseentity"></a>

```json
{
  "data": [
    {
      "fields": [
        {
          "fieldType": 0,
          "isRequired": true,
          "name": "string"
        }
      ],
      "issuerKey": {
        "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
        "value": "a860a344-d7b2-406e-828e-8d442f23f344"
      },
      "issuerName": "string",
      "key": {
        "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
        "value": "a860a344-d7b2-406e-828e-8d442f23f344"
      },
      "schemaKey": {
        "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
        "value": "a860a344-d7b2-406e-828e-8d442f23f344"
      },
      "schemaName": "string"
    }
  ],
  "pageNumber": 0,
  "pageSize": 0,
  "totalCount": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[SchemaVerifierDto](#schemaschemaverifierdto)]¦null|false|none|none|
|pageNumber|integer(int32)|false|none|none|
|pageSize|integer(int32)|false|none|none|
|totalCount|integer(int32)|false|none|none|

<h2 id="tocS_SchemaVerifierKey">SchemaVerifierKey</h2>
<!-- backwards compatibility -->
<a id="schemaschemaverifierkey"></a>
<a id="schema_SchemaVerifierKey"></a>
<a id="tocSschemaverifierkey"></a>
<a id="tocsschemaverifierkey"></a>

```json
{
  "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
  "value": "a860a344-d7b2-406e-828e-8d442f23f344"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|guid|string(uuid)|false|none|none|
|value|string(uuid)|false|none|none|

<h2 id="tocS_VerificationDto">VerificationDto</h2>
<!-- backwards compatibility -->
<a id="schemaverificationdto"></a>
<a id="schema_VerificationDto"></a>
<a id="tocSverificationdto"></a>
<a id="tocsverificationdto"></a>

```json
{
  "openIdVerificationOffer": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|openIdVerificationOffer|string¦null|false|none|none|