---
title: Home
layout: home
nav_order: 1
---

<!-- <button class="btn js-toggle-dark-mode">Preview dark color scheme</button> -->

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Preview dark color scheme';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Return to the light side';
  }
});
</script>

# UltraPass Documentation

Welcome to the **UltraPass Docs**. This is where you can find everything you need to know about how to integrate with UltraPass, your go-to platform for identity and credential solutions.

## What is UltraPass? 

UltraPass is a Trust Platform that enables you to quickly deploy identity and credential solutions at scale, using the power of verifiable credentials. Verifiable credentials are digital representations of claims that can be cryptographically verified by any relying party. For example, a verifiable credential can represent an identity document, a diploma, a health record, or any other type of data that needs to be trusted and verified.

UltraPass allows you to create, issue, verify, and exchange verifiable credentials across ecosystems, using open standards and protocols. UltraPass also provides you with tools and services to manage your identity and credential authflows, such as credential schemas, digital wallets, identity verification, biometrics, and more.

With UltraPass, you can:

- Enhance your security, privacy, and interoperability with verifiable credentials
- Streamline your data sharing and verification processes
- Reduce your operational costs and complexity
- Improve your customer experience and satisfaction
- Innovate and collaborate with other identity and credential providers

## Why use UltraPass?

UltraPass offers several benefits for Organizations who want to integrate with verifiable credentials, such as:

- **Speed**: UltraPass allows you to launch your identity and credential solutions in minutes, without the need for complex coding or infrastructure. You can use our Portal, API platform, or SDKs to easily integrate with UltraPass.
- **Flexibility**: UltraPass supports various formats and channels for credential exchange. You can also customize your schemas, authflows, UX, and branding to suit your needs.
- **Scalability**: UltraPass can handle any volume of credential transactions, thanks to our cloud-based architecture and distributed ledger technology.
- **Reliability**: UltraPass ensures the availability, consistency, and integrity of your identity and credential transactions.
- **Compliance**: UltraPass adheres to the latest data protection regulations and standards. Users remain in control of their data.

## How to get started?

To get started with UltraPass, you need to follow these steps:

1. Register for an account on the [UltraPass Portal](https://portal.ultrapassid.com), where you can manage your Organization and configure products.
2. Explore our [Portal Guide](https://docs.ultrapassid.com/docs/portal), where you can find step-by-step instructions on how to create your first schema, issue your first credential, authenticate users, and more.
3. Browse our [Technical Documentation](https://docs.ultrapassid.com/docs/api-reference), where you can find detailed guides, tutorials, references, and examples on how to integrate with our API platform.
4. Contact us if you have any questions or feedback. We are always happy to hear from you.

We hope you enjoy using UltraPass and join us in building a more secure, private, and convenient digital world. Thank you for choosing UltraPass! 
