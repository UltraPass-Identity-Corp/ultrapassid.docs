---
layout: default
title: "Architecture & Data Flow"
parent: AirLink
nav_order: 1
last_modified_date: 2025-08-20
---

# Architecture & Data Flow — AirLink Mobile SDK

The AirLink SDK is a modular, on-device mobile SDK for document capture, biometric matching, credential issuance/verification, and integration with travel/identity ecosystems.

# Diagram
![AirLink Architecture](../../../assets/images/AirLink_Architecture.png "AirLink Architecture")


## Core Components

- **Mobile App (Host Application)**  
  Integrates the AirLink SDK and manages passenger interactions, including check-in, identity verification, and credential presentation.

- **AirLink SDK Modules**
  - **Biometric Module**  
    On-device selfie capture, liveness detection, and 1:1 facial matching.
  - **Document & Credential Verification**  
    MRZ/OCR scanning, NFC passport chip reading, and digital credential verification.
  - **External Services Integration**  
    Adapters for IATA services (Timatic AutoCheck, Contactless Travel Directory), national ID verification, and third-party APIs.
  - **Digital Wallet**  
    Secure storage and retrieval of verifiable credentials for use across the travel journey.

- **External Systems**
  - **IATA Services** (Timatic AutoCheck, Contactless Travel Directory)
  - **National ID Verification** (e.g., eVerify)
  - **Airport Systems** (biometric bag-drop, touchless security, boarding gates)


## Data Flow

1. **Passenger Check-In**  
   The passenger launches the airline app and begins the check-in process. The app provides itinerary and boarding pass data to the AirLink SDK.

2. **Travel Requirements & Airport Capability Check**  
   - AirLink queries the **IATA Contactless Travel Directory** to determine biometric capabilities at departure, transit, and arrival airports.
   - It checks **Timatic AutoCheck** to validate travel document requirements, visa rules, and health regulations based on the passenger’s itinerary.

3. **Identity Verification & Document Collection**  
   - The SDK guides the user through capturing their passport or national ID using OCR and NFC.
   - A selfie is captured with liveness detection, followed by a 1:1 facial match against the document photo.
   - Identity is optionally validated against national ID systems or third-party verification services.

4. **Credential Issuance**  
   - Based on verified identity and travel eligibility, AirLink issues verifiable credentials (e.g., digital ID, travel pass).
   - Credentials are stored securely in the on-device digital wallet for later use.

5. **Biometric Enrollment for Airport Use**  
   - With user consent, AirLink facilitates **off-airport enrollment** into supported airport biometric systems.
   - This enables touchless experiences at bag-drop, security, and boarding—without needing to present physical documents again.

## Security & Privacy

- **On-Device Processing**  
  All biometric and document data is processed locally to protect user privacy.

- **Secure Storage**  
  Sensitive data is encrypted using platform-native secure storage (Keychain on iOS, EncryptedSharedPreferences on Android).

- **Secure Communication**  
  All network traffic is encrypted via HTTPS, with authentication tokens stored securely.

- **Privacy-First Design**  
  Built on decentralized identity principles, AirLink ensures user control over personal data and supports selective disclosure via verifiable credentials.

---

Refer to the Architecture Overview and platform-specific SDK guides for implementation details and integration best practices.
