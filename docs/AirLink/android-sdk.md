---
title: "Android SDK Reference (Kotlin)"
parent: AirLink
nav_order: 3
last_modified_date: 2025-08-20
---

# AirLink Android SDK — Kotlin Reference & Examples

This guide provides Kotlin (Android) integration details for the AirLink SDK, mapping TypeScript sample interfaces to idiomatic Kotlin and coroutines.

## 1. Quick Start
- Add SDK artifact (placeholder):
  - `implementation "com.ultrapass:airlink:1.0.0"`
- Add permissions in AndroidManifest: CAMERA, NFC, INTERNET
- Use EncryptedSharedPreferences or Keystore for secrets
- No API key is required. AirLink authenticates backend calls using device/app attestation (see below).

## 2. Key Types & Mapping
- `AirLink` (object): modules for `compliance`, `identity`, `credentials`, `boardingPass`
- `AirLinkConfig` data class: environment, timeout, baseUrl
- `PassportData` data class: MRZ, document info, images
- `HttpClient` interface: suspend functions

## 3. Initialization Example
```kotlin
suspend fun setupAirLink() {
  val config = AirLinkConfig(environment = Environment.SANDBOX, timeout = 30_000)
  AirLink.initialize(config)
  Log.d("AirLink", "initialized: ${AirLink.getVersion()}")
}
```
## 3a. Device/App Attestation for Backend Authentication

AirLink uses device/app attestation to authenticate backend API calls instead of static API keys. The SDK obtains an attestation token from the platform (e.g., Play Integrity API or SafetyNet on Android) and includes it with each backend request. The backend validates the attestation token to ensure requests originate from a genuine, unmodified app on a real device.

**Benefits:**
- No static secrets embedded in the app
- Attestation tokens are short-lived and cannot be reused
- Backend access is restricted to genuine app instances

**Implementation outline:**
1. The SDK requests an attestation token from the platform attestation service at runtime.
2. The SDK exchanges the attestation token for a short-lived JWT which it sends with each backend API call.
3. The backend verifies the attestation token before processing the request.

## 4. Passport NFC Read Example
```kotlin
try {
  val options = PassportNFCOptions(includeImages = true, requestedDataGroups = listOf("DG1","DG2","DG11","DG14"))
  val result: PassportData = AirLink.identity.passport.nfcReader.readData(bacKey = mrz, options = options)
  // handle result
} catch (e: AirLinkException) {
  // handle error
}
```
- Add NFC permission and handle NFC intents

## 5. Selfie Capture & Biometric Verification
```kotlin
lifecycleScope.launch {
  try {
    val photo: PhotoFile = AirLink.identity.selfie.takePhoto(PreferredCamera.FRONT, Quality.HIGH)
    AirLink.identity.passport.verifyPassportWithSelfie(passportDG2Photo = passportPhoto, selfie = photo)
  } catch (e: Exception) {
    Log.e("AirLink", "Selfie capture or verification error", e)
  }
}
```

## 6. Compliance & Credential Usage
```kotlin
suspend fun validateOwnership() {
  AirLink.compliance.validateDocumentsOwnership(
    passportName = "Alice Example",
    boardingPassName = "Alice Example",
    visaName = null,
    visaPassportNumber = null,
    actualPassportNumber = "X123456"
  )
}

val req = TravelComplianceRequest(nationality="GBR", passportType="P", itinerary = itinerary, purposeAndStayDuration = 7)
val resp = AirLink.compliance.verifyTravelCompliance(req)
```
- Issue/store VCs using SDK wallet API

## 7. Storage, Logging & HTTP Client
- Use EncryptedSharedPreferences/Keystore for secrets/VCs
- Implement `HttpClient` interface (OkHttp/Retrofit)
- Implement `AuditLogger` for user action logs

## 8. Permissions & Privacy
- Request runtime permissions (CAMERA, NFC)
- Encrypt all PII; provide user data deletion option
- Use TLS for all network calls

## 9. Error Handling & Concurrency
- Suspend functions throw typed exceptions (permission, camera, NFC, network)
- Use structured concurrency and timeouts

> **Note:** Production apps must implement robust camera, NFC, and secure storage integrations.
