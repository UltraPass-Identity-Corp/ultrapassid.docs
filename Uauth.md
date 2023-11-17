---
layout: default
title: UAuth
nav_order: 2
---
---
title: Client Api v1.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

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

```shell
# You can also use wget
curl -X POST https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'x-upid-organization-key: API_KEY'

```

```http
POST https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session HTTP/1.1
Host: dev-clientapi-a53fz2ohf.azurewebsites.net
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{"workflowKey":"322dbc7a-0a8a-452a-ba6d-c3e893f29ecc"}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'x-upid-organization-key':'API_KEY'
};

fetch('https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'x-upid-organization-key' => 'API_KEY'
}

result = RestClient.post 'https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'x-upid-organization-key': 'API_KEY'
}

r = requests.post('https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'x-upid-organization-key' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "x-upid-organization-key": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

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

```shell
# You can also use wget
curl -X GET https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId} \
  -H 'Accept: application/json' \
  -H 'x-upid-organization-key: API_KEY'

```

```http
GET https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId} HTTP/1.1
Host: dev-clientapi-a53fz2ohf.azurewebsites.net
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'x-upid-organization-key':'API_KEY'
};

fetch('https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'x-upid-organization-key' => 'API_KEY'
}

result = RestClient.get 'https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'x-upid-organization-key': 'API_KEY'
}

r = requests.get('https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'x-upid-organization-key' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "x-upid-organization-key": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://dev-clientapi-a53fz2ohf.azurewebsites.net/api/uauth/session/{sessionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

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

