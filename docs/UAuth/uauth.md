---
layout: default
title: UAuth
nav_order: 2
has_children: true
permalink: /docs/uauth
last_modified_date: %H%M%S
---

Use **UAuth** to authenticate and store user data.

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