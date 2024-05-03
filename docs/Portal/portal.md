---
layout: default
title: Portal
nav_order: 3
permalink: /docs/portal
---

# UltraPass Portal

## Overview
The UltraPass Portal streamlines the management of your Organization's configurations and Products, ensuring a seamless administrative experience.

## Organizations
An Organization is an entity within UltraPass that includes a billing profile, domain, users, and product configurations. To extend an invitation to potential users, they must possess a valid email address associated with the Organization's domain.

### User Permissions
Authorized users are empowered to manage TrustLink Schemas, UAuth Identity Flows, and review platform logs and mertics; maintaining the integrity and functionality of the Organization's operations.

## API Keys
API Keys serve as a secure method of authenticating to the UltraPass APIs on behalf of an Organization. These keys are unique to each Organization and are essential for maintaining the security of transactions. API Keys can be found in the UltraPass Portal.

### Key Management
- **Confidentiality**: API Keys are sensitive and should be safeguarded with the utmost confidentiality.
- **Rotation Policy**: Frequent rotation of API Keys is recommended to enhance security. Organizations are equipped with a Primary and Secondary key, both of which can be rotated independently.
- **Usage**: To utilize an API Key, it must be included in the `x-upid-api-key` header for all requests.

Remember to adhere to these guidelines to ensure the security and efficiency of your Organization's operations.

## Logs

### Audit & Security

Audit & Security logs are designed to provide comprehensive insights into user activities and API interactions within the UltraPass Platform. These logs are crucial for monitoring, securing the platform, and meeting complaiance standards.

- **User Activity:** Every action performed by a user within the portal is logged, detailing the timestamp, user ID, and the specific action taken.
- **Client API Interactions:** All API calls made by clients are recorded; including the endpoint accessed and request metedata.

### Usage

Usage logs offer a detailed record of product consumption related to credential management and authentication processes, such as:

- **Credential Issuance & Verification:** Logs every instance of credential issuance and verification, capturing the Schema used, timestamp, and organization details.
- **UAuth Logins:** Captures each successful UAuth login attempt, providing data on the unique identifier, timestamp, and application context involved in the authentication process.

These logs are essential for analyzing product usage patterns, identifying trends, and making informed decisions about resource allocation and system improvements.

{: .fs-6 .fw-300 }