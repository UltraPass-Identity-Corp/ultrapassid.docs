---
layout: default
title: UAuth
parent: API Reference
nav_order: 2
---
<!-- Generator: Widdershins v4.0.1 -->

<h1 id="client-api">Client Api v1.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

UltrapassId Client Api

Base URLs:

* <a href="https://dev-clientapi-a53fz2ohf.azurewebsites.net/api">https://dev-clientapi-a53fz2ohf.azurewebsites.net/api</a>

Web: <a href="https://ultrapassid.com/">UltrapassId</a> 

# Authentication

* API Key (x-upid-organization-key)
    - Parameter Name: **x-upid-organization-key**, in: header. 

<h1 id="client-api-uauth">UAuth</h1>

## CacheWorkflowInstanceSession

<a id="opIdCacheWorkflowInstanceSession"></a>

> Code samples

```http
POST https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session HTTP/1.1
Host: dev-clientapi-a53fz2ohf.azurewebsites.net
Content-Type: application/json
Accept: application/json

```

`POST /uauth/session`

> Body parameter

```json
"{\"workflowKey\":\"322dbc7a-0a8a-452a-ba6d-c3e893f29ecc\"}"
```

<h3 id="cacheworkflowinstancesession-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[cacheWorkflowSessionCommand](#schemacacheworkflowsessioncommand)|true|Caches a provided Workflow Instance|

> Example responses

> 201 Response

```json
"{\"getSessionUrl\":\"https://auth.ultrapassid.com/uauth?sessionId=c849466775754912bbc9058e627925f0\"}"
```

<h3 id="cacheworkflowinstancesession-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Session has been cached|[cacheWorkflowSessionResponse](#schemacacheworkflowsessionresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request not valid|string|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Workflow not valid for this Organization|string|
|424|[Failed Dependency](https://tools.ietf.org/html/rfc2518#section-10.5)|Dependent Workflow exception|string|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
x-upid-organization-key
</aside>

## GetCachedWorkflowInstance

<a id="opIdGetCachedWorkflowInstance"></a>

> Code samples

```http
GET https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId} HTTP/1.1
Host: dev-clientapi-a53fz2ohf.azurewebsites.net
Accept: application/json

```

`GET /uauth/session/{sessionId}`

<h3 id="getcachedworkflowinstance-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|sessionId|path|string|true|Existing SessionId|

> Example responses

> 200 Response

```json
"{\"workflowKey\":\"322dbc7a-0a8a-452a-ba6d-c3e893f29ecc\",\"policyId\":\"B2C_1A_UUID_REGISTRATION\",\"clientRedirectUrl\":\"https://dev-portal.ultrapassid.com\"}"
```

<h3 id="getcachedworkflowinstance-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The cached Workflow|[getCachedWorkflowSessionResponse](#schemagetcachedworkflowsessionresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request not valid|string|
|424|[Failed Dependency](https://tools.ietf.org/html/rfc2518#section-10.5)|Dependent Workflow exception|string|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
x-upid-organization-key
</aside>

# Schemas

<h2 id="tocS_cacheWorkflowSessionCommand">cacheWorkflowSessionCommand</h2>
<!-- backwards compatibility -->
<a id="schemacacheworkflowsessioncommand"></a>
<a id="schema_cacheWorkflowSessionCommand"></a>
<a id="tocScacheworkflowsessioncommand"></a>
<a id="tocscacheworkflowsessioncommand"></a>

```json
"{\"workflowKey\":\"322dbc7a-0a8a-452a-ba6d-c3e893f29ecc\"}"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|workflowKey|string(uuid)|false|none|none|

<h2 id="tocS_cacheWorkflowSessionResponse">cacheWorkflowSessionResponse</h2>
<!-- backwards compatibility -->
<a id="schemacacheworkflowsessionresponse"></a>
<a id="schema_cacheWorkflowSessionResponse"></a>
<a id="tocScacheworkflowsessionresponse"></a>
<a id="tocscacheworkflowsessionresponse"></a>

```json
"{\"getSessionUrl\":\"https://auth.ultrapassid.com/uauth?sessionId=c849466775754912bbc9058e627925f0\"}"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|workflowInstanceSessionDto|[workflowInstanceSessionDto](#schemaworkflowinstancesessiondto)|false|none|none|

<h2 id="tocS_getCachedWorkflowSessionResponse">getCachedWorkflowSessionResponse</h2>
<!-- backwards compatibility -->
<a id="schemagetcachedworkflowsessionresponse"></a>
<a id="schema_getCachedWorkflowSessionResponse"></a>
<a id="tocSgetcachedworkflowsessionresponse"></a>
<a id="tocsgetcachedworkflowsessionresponse"></a>

```json
"{\"workflowKey\":\"322dbc7a-0a8a-452a-ba6d-c3e893f29ecc\",\"policyId\":\"B2C_1A_UUID_REGISTRATION\",\"clientRedirectUrl\":\"https://dev-portal.ultrapassid.com\"}"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|workflowInstanceSessionResponse|[workflowInstanceSessionResponseDto](#schemaworkflowinstancesessionresponsedto)|false|none|none|

<h2 id="tocS_workflowInstanceSessionDto">workflowInstanceSessionDto</h2>
<!-- backwards compatibility -->
<a id="schemaworkflowinstancesessiondto"></a>
<a id="schema_workflowInstanceSessionDto"></a>
<a id="tocSworkflowinstancesessiondto"></a>
<a id="tocsworkflowinstancesessiondto"></a>

```json
{
  "getSessionUrl": "http://example.com"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|getSessionUrl|string(uri)|false|none|none|

<h2 id="tocS_workflowInstanceSessionResponseDto">workflowInstanceSessionResponseDto</h2>
<!-- backwards compatibility -->
<a id="schemaworkflowinstancesessionresponsedto"></a>
<a id="schema_workflowInstanceSessionResponseDto"></a>
<a id="tocSworkflowinstancesessionresponsedto"></a>
<a id="tocsworkflowinstancesessionresponsedto"></a>

```json
{
  "workflowKey": {
    "guid": "ee6a7af7-650d-499b-8e32-58a52ffdb7bc",
    "value": "a860a344-d7b2-406e-828e-8d442f23f344"
  },
  "policyId": "string",
  "clientRedirectUrl": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|workflowKey|[workflowKey](#schemaworkflowkey)|false|none|none|
|policyId|string|false|none|none|
|clientRedirectUrl|string|false|none|none|

<h2 id="tocS_workflowKey">workflowKey</h2>
<!-- backwards compatibility -->
<a id="schemaworkflowkey"></a>
<a id="schema_workflowKey"></a>
<a id="tocSworkflowkey"></a>
<a id="tocsworkflowkey"></a>

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

