---
layout: default
title: "Android SDK Reference (Kotlin)"
parent: AirLink
nav_order: 3
last_modified_date: 2025-08-25
---

# AirLink Android SDK — Kotlin Reference & Examples

This guide provides Kotlin (Android) integration details for the AirLink SDK, mapping TypeScript sample interfaces to idiomatic Kotlin and coroutines.

## Quick Start

- **Add SDK Dependency**: Add the AirLink SDK to your app's `build.gradle` file:
  ```groovy
  implementation "com.ultrapass:airlink:1.0.0"
  ```
- **Permissions**: Declare the following permissions in your `AndroidManifest.xml`:
  - `CAMERA`
  - `NFC`
  - `INTERNET`
- **Secure Storage**: Use `EncryptedSharedPreferences` or the Android Keystore for storing sensitive data.
- **Authentication**: No API key is required. AirLink authenticates backend calls using device and app attestation.

## Key Types

- **`AirLink`**: The main entry point object, providing access to modules for `compliance`, `identity`, `credentials`, and `boardingPass`.
- **`AirLinkConfig`**: A data class for configuring the SDK, including `environment`, `timeout`, and `baseUrl`.
- **`PassportData`**: A data class containing passport information such as the MRZ, document details, and images.
- **`HttpClient`**: An interface for implementing network requests using suspend functions.

## Initialization

To use the AirLink SDK, you must first initialize it with a configuration.

```kotlin
suspend fun setupAirLink() {
  val config = AirLinkConfig(environment = Environment.SANDBOX, timeout = 30_000)
  AirLink.initialize(config)
  Log.d("AirLink", "AirLink SDK initialized. Version: ${AirLink.getVersion()}")
}
```

## Device/App Attestation for Backend Authentication

AirLink uses device and app attestation to authenticate backend API calls instead of static API keys. The SDK obtains an attestation token from the platform (e.g., Play Integrity API on Android) and includes it with each backend request. The backend validates this token to ensure requests originate from a genuine, unmodified app on a real device.

**Benefits:**
- Eliminates the need to embed static secrets in the app.
- Attestation tokens are short-lived and cannot be reused.
- Restricts backend access to genuine instances of your app.

**Implementation Outline:**
1. The SDK requests an attestation token from the platform's attestation service at runtime.
2. The SDK exchanges the attestation token for a short-lived JWT, which is sent with each backend API call.
3. The backend verifies the JWT before processing the request.

## Passport NFC Reading

Read data from an ePassport's NFC chip. This requires the user to grant NFC permission and for your app to handle NFC intents.

```kotlin
try {
  val options = PassportNFCOptions(
    includeImages = true, 
    requestedDataGroups = listOf("DG1", "DG2", "DG11", "DG14")
  )
  val result: PassportData = AirLink.identity.passport.nfcReader.readData(bacKey = mrz, options = options)
  // Process the passport data
} catch (e: AirLinkException) {
  // Handle NFC reading errors
}
```

## Selfie Capture & Biometric Verification

Capture a selfie and perform a biometric verification against the photo from the passport.

```kotlin
lifecycleScope.launch {
  try {
    val photo: PhotoFile = AirLink.identity.selfie.takePhoto(PreferredCamera.FRONT, Quality.HIGH)
    val verificationResult = AirLink.identity.passport.verifyPassportWithSelfie(
      passportDG2Photo = passportPhoto, 
      selfie = photo
    )
    // Process verification result
  } catch (e: Exception) {
    Log.e("AirLink", "Selfie capture or verification failed", e)
  }
}
```

## Compliance & Credential Usage

Perform compliance checks and manage Verifiable Credentials (VCs).

### Document Ownership Validation
```kotlin
suspend fun validateOwnership() {
  val isValid = AirLink.compliance.validateDocumentsOwnership(
    passportName = "Alice Example",
    boardingPassName = "Alice Example",
    visaName = null,
    visaPassportNumber = null,
    actualPassportNumber = "X123456"
  )
  // Handle validation result
}
```

### Travel Compliance Verification
```kotlin
val request = TravelComplianceRequest(
  nationality = "GBR", 
  passportType = "P", 
  itinerary = itinerary, 
  purposeAndStayDuration = 7
)
val response = AirLink.compliance.verifyTravelCompliance(request)
// Process compliance response
```
- Use the SDK's wallet API to issue and store VCs.

## Error Handling & Concurrency

- The SDK's suspend functions throw typed exceptions for specific errors (e.g., permission, camera, NFC, network).
- Use structured concurrency (e.g., `viewModelScope`, `lifecycleScope`) and coroutine timeouts to build a robust and responsive user experience.
