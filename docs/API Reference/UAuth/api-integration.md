---
layout: default
title: API Integration
parent: UAuth
nav_order: 3
---
<h1 id="-uauth">UAuth</h1>

> Create sessions and trigger UAuthFlows at the returned sessionURL. Your application must be prepared to receive the session reponse at the redirectURL configured in the Portal for the corresponding UAuthFlow.

## CreateUAuthFlowSession

<a id="opIdCacheWorkflowInstanceSession"></a>

> Code samples

```http
POST /uauth/session HTTP/1.1

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

|Status|Meaning|Description|Model|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Session has been cached|[cacheWorkflowSessionResponse](#schemacacheworkflowsessionresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request not valid|string|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Workflow not valid for this Organization|string|
|424|[Failed Dependency](https://tools.ietf.org/html/rfc2518#section-10.5)|Dependent Workflow exception|string|

<aside class="warning">
</aside>

# Models

<h2 id="tocS_cacheWorkflowSessionCommand">createUAuthFlowSessionCommand</h2>

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

<h2 id="tocS_cacheWorkflowSessionResponse">createUAuthFlowSessionResponse</h2>

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

<h2 id="tocS_workflowInstanceSessionDto">workflowInstanceSessionDto</h2>

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