---
layout: default
title: UAuth Application Registration
parent: UAuth
nav_order: 1
last_modified_date: 2024-05-02
---

# UAuth Registered App

In order to utilize UAuth's privacy preserving reusable digital identities and Identity Flows, you need to register applications in the UltraPass Portal. To create a UAuth Registered App in the UltraPass Portal, follow these steps below:

1. **Create a New App Registration**: Navigate to UAuth Registered Apps in the UltraPass Portal and select "Register a New Application".
<br>
![Register New Application](../../../assets/images/RegisterNewApplication.png "Register New Application")

2. **Provide Registered App Details**: Assign a unique friendly name to your application that easily identifies it among others. This name will be used in the list of registered applications and can be changed later if needed. Also define one or more Redirect URIs where your application will receive authorization codes and token responses. Once complete, click "Save".
    > *Your application will need to be capable of handling authorization code and token responses at these defined Redirect URIs in compliance with the OIDC Standard Authorization Code Flow with PKCE.*

    ![Registered App Details](../../../assets/images/RegisteredAppDetails.png "Registered App Details")

3. **View Registered App Configuration**: After successful creation of the UAuth Registered App, a unique "ClientId" will be created and displayed in the Portal. You will use this ClientId during UAuth integration. You may update the Registered App configuration at any time. In order to change ClientId, a new Registered App must be created.
<br>
![View Registered App Config](../../../assets/images/ViewRegisteredAppConfig.png "View Registered App Config")

It is important to ensure the configured settings are correct. The defined Redirect URIs are critical in the successful integration of your application with UltraPass UAuth.

For additional information on how to integrate UAuth, please review our [UAuth Integration](https://docs.ultrapassid.com/docs/API%20Reference/uauth.html) documentation.