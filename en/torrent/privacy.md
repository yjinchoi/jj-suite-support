---
layout: default
lang: en
title: "Privacy Policy — Easy NAS Download Manager"
permalink: /en/torrent/privacy/
alt: /torrent/privacy/
app: torrent
kind: privacy
description: "What information Easy NAS Download Manager handles, where it is stored and who it talks to."
---

# Privacy Policy

**Applies to**: Easy NAS Download Manager (iOS)
**Last updated**: 2026-10-21 **Version**: 1.2

---

## 1. Summary

The developer does not collect any user data.

There is no developer-operated server, and the app has no network connection to the developer. Your data moves between your device and the servers or websites you choose to connect to. The developer has no access to it.

To keep the app free, it displays Google AdMob ads. When loading ads, Google's advertising SDK in the app sends certain device data directly to Google (§6.1). The app asks once for iOS App Tracking Transparency (ATT) permission. The advertising identifier (IDFA) is shared with Google for personalized ads only if you grant this permission; otherwise, the app requests only non-personalized ads (§6.1). In-app purchases to remove ads are processed by Apple's App Store (§6.2).

## 2. Principles

- **Tracking occurs only with your permission.** The app requests App Tracking Transparency permission once. If you allow it, the advertising SDK uses the advertising identifier (IDFA) to request personalized ads, which constitutes tracking under Apple's policy. If you do not allow it (whether denied, not yet decided, or restricted), the IDFA is not shared and all ad requests are sent as non-personalized (`npa=1`). The app's own code never reads the advertising identifier or any other device identifier. You can change this permission at any time in iOS Settings > Privacy & Security > Tracking.
- **No analytics or crash-reporting SDKs.** The app does not include any third-party analytics or crash-reporting libraries. The only bundled third-party SDK for advertising is the Google Mobile Ads SDK (which includes the User Messaging Platform for consent management); the data it handles is described in §6.1.
- **No data is sent to the developer.** Usage history, device information, error reports, and purchase details are never transmitted to the developer.
- **No sale or sharing of user data.** Because the developer does not collect or hold any user data, nothing is sold or shared with third parties. Data sent directly to Google by the advertising SDK is covered in §6.1.

## 3. What the app stores on your device

### 3.1 iOS Keychain

The app uses the iOS Keychain to store sensitive data securely. The specific items stored vary by app and are detailed in the per-app section below.

All three apps apply the same security rules:

- Items are saved with the `kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly` accessibility setting.
  - `ThisDeviceOnly`: Items are not synced via iCloud Keychain and are excluded from device backups. They remain strictly on the device.
  - `AfterFirstUnlock`: The app can read these items while the screen is locked, provided the device has been unlocked at least once after a reboot.
- Credentials and certificate trust settings are isolated per app. Each app writes to its own dedicated Keychain access group, preventing one app from reading another app's passwords, accounts, or trusted certificates.
- The only exception is the ad-free purchase status. If you purchase ad removal in one app, ads are also removed in the other two apps on the same device. To support this, all three apps share an access group (`com.jjsuite.shared`) where each app records a single entry containing only the ad-free status (none, expiration date, or lifetime) and the last update timestamp. No payment details, Apple ID, or receipts are stored. This sharing is limited to apps from this developer installed on the same device.
- iOS does not always remove Keychain items automatically when an app is deleted. If you want to ensure your saved credentials are completely removed, please delete them within the app before uninstalling it (§9). The ad-free status remains in the Keychain after uninstallation so that it continues to apply to the other two apps.

### 3.2 App preferences (UserDefaults)

General preferences such as appearance (light/dark), sort order, and display options are stored in standard local storage (UserDefaults) and are accessible only to the app itself. Your ad-consent status (§6.1) is also stored here by Google's consent SDK.

### 3.3 Files on the device

Files created by the app or saved by you remain on your device, either in the app's sandbox or, depending on the app, in a shared container used by this developer's apps (see the per-app section). The app reads file creation and modification timestamps within its own container to sort and display files and to rotate diagnostic logs.

## 4. What goes to iCloud — settings only

The app uses Apple's iCloud Key-Value Store to sync select preferences across your devices.

- Synced data: preference values such as feature toggles, selected options (e.g., appearance or search engine), numeric settings, default folder path strings, and the active profile identifier (UUID).
- Excluded data: passwords and other credentials, the contents of photos, videos, or documents, browsing history, bookmarks, diagnostic logs, ad-free purchase records, and ad-consent status.
- Each app uses its own isolated iCloud store and cannot overwrite another app's settings.
- Syncing is managed by Apple. Your settings remain in your personal iCloud account, and the developer has no access to them.
- There is no in-app switch for iCloud sync, but you can disable it at any time by turning off iCloud for the app in iOS Settings.

The exact list and number of synced preference keys vary by app and are detailed in the per-app section.

## 5. Diagnostic log

The app maintains a local diagnostic log on your device to assist with troubleshooting.

- Location: saved as per-session text files in `Documents/diagnostics/` inside the app container. Only the 10 most recent session files are retained.
- No automatic transmission: logs are never sent automatically. They leave your device only if you manually export them using the share sheet in Settings.
- What may be logged: operation timestamps and results, error messages, the addresses and request paths of servers contacted by the app, and target URLs of failed requests. At the start of each session, one line records the device model, iOS version, and app version to help reproduce issues; this does not include any unique device identifier.
- What is excluded: passwords and two-factor authentication seeds are never logged, and server session keys are masked before being written to disk.

If you attach a diagnostic log to a support email, please note that the information above will be included. You may always contact support without attaching a log.

## 6. Who the app talks to

The app makes network connections only to destinations that you configure or open yourself, as well as two external services: Google for serving ads (§6.1) and Apple's App Store for processing ad-free purchases (§6.2). User-configured destinations vary by app and are listed in the per-app section.

Across all three apps, there is no developer-operated server, and the app never sends requests to the developer.

### 6.1 Ads — Google AdMob

- **When ads appear**: Ads are shown only while you are waiting for an operation to finish, such as connecting to a server, transferring files, or adding a task. A 300×250 banner labeled "Ad" is displayed inside the progress dialog for at least 2 seconds. There are no launch ads, no timed interstitial ads, and no ads during the first 5 seconds after opening the app. If you have purchased ad removal, if ad consent has not been completed, or if no ad is ready, the dialog simply shows the progress state.
- **Tracking permission (ATT) and personalized ads**: On first launch, after completing the regional consent check below, the app presents the iOS App Tracking Transparency prompt once while the app is active.
  - If you allow tracking, your advertising identifier (IDFA) is shared with Google, and you may receive personalized ads based on your interests and activity across other apps and websites. Under Apple's guidelines, this constitutes tracking.
  - If you do not allow tracking (or if tracking is restricted on your device), the IDFA is withheld and all ad requests include the non-personalized flag (`npa=1`).
  - App functionality and ad frequency remain the same regardless of your choice. You can update your preference at any time in iOS Settings > Privacy & Security > Tracking.
- **Regional consent**: At startup, the app uses Google's User Messaging Platform to check whether regional privacy regulations apply. In the European Economic Area (EEA), the UK, and similar jurisdictions, Google's consent form is presented before any ads are requested. No ad requests are made without confirmed consent. You can review or change your consent choices at any time in Settings > Remove Ads > Ad Privacy Settings (this option is visible only in regions where consent is required).
- **Data processed by Google** (per Google's AdMob disclosures): device identifiers, advertising data (ads viewed and tapped), product interactions (app launches and taps), coarse location (inferred from your IP address), and diagnostics (performance and crash data). Google uses this information to serve and measure ads, prevent fraud, and perform analytics. Device identifiers (specifically the IDFA, if you allow tracking) may be used for tracking, and coarse location, advertising data, product interactions, and device identifiers may be linked to your identity by Google. If you decline tracking, the IDFA is not provided.
- All ad-related data is sent directly from the Google SDK in the app to Google's servers. It never passes through a developer server, and the developer only sees aggregate statistics such as total impressions and earnings in the AdMob console.
- Tapping an ad opens the advertiser's website or App Store listing, which is governed by that third party's own privacy policy.
- For more details on how Google handles data, please see the [Google Privacy Policy](https://policies.google.com/privacy) and [How Google uses information from sites or apps that use its services](https://policies.google.com/technologies/partner-sites).

### 6.2 Ad-free purchase — Apple App Store

- The app offers three in-app purchase options to remove ads: 1-month and 1-year passes (non-renewing, so they never auto-charge) and a lifetime pass (one-time purchase).
- All payments are processed by Apple through the App Store. Neither the app nor the developer receives your payment details, credit card number, Apple ID, or any other personally identifiable buyer information.
- The app uses Apple's StoreKit framework to check on-device purchase records (product ID, purchase date, and refund status) to calculate your active ad-free period, and saves only the resulting status and expiration date to the shared Keychain item described in §3.1.
- Tapping "Restore Purchases" syncs with the App Store to retrieve your previous purchase records.

## 7. Security

- **Encrypted connections by default**: Whenever supported by the destination server, the app communicates over standard HTTPS (TLS).
- **Plain HTTP exceptions**: All three apps set `NSAllowsArbitraryLoads = true` so they can connect to destinations that only support unencrypted HTTP. The specific scenarios where plain HTTP is used, and the reasons for them, are explained in the per-app section. In all cases, the destination is either a website you opened directly or a personal server whose address you entered yourself; no traffic ever goes to the developer (§6).
- **Encryption and export compliance**: The app relies solely on standard encryption protocols (TLS, plus SSH and SMB 3 in applicable apps) and completes Apple's App Store export compliance declarations in accordance with U.S. export regulations. App-specific declarations are noted in the per-app section.
- **Credential storage**: Login credentials are stored in the iOS Keychain as outlined in §3.1.
- **Certificate verification**: When you explicitly choose to trust a host with a self-signed or untrusted certificate, the app saves that certificate's fingerprint and verifies it on subsequent connections. Certificate errors for unapproved hosts are blocked.

## 8. Children's privacy (COPPA)

The developer does not collect personal information from anyone, including children under the age of 13, and the app is not directed at children. Personalized ads are requested only when tracking permission is granted; otherwise, only non-personalized ads are served. Data transmitted to Google by the advertising SDK is covered in §6.1, while all other data remains on your device and your own servers.

## 9. Your control and how to delete data

- **Uninstalling the app**: Deleting the app removes its local sandbox files and preferences. If the app uses a shared storage container with another app from this developer, files in that shared container remain on the device as long as any sibling app using it stays installed (see the per-app section). For Keychain retention details, see §3.1.
- **Clearing data within the app**: You can delete stored data directly from the app's Settings screen. Available deletion options and their menu locations are listed in the per-app section.
- **Disabling iCloud settings sync**: Open iOS Settings > [your name] > iCloud, and turn off iCloud access for this app.
- **Revoking tracking permission**: Turn off the app's switch in iOS Settings > Privacy & Security > Tracking. All subsequent ad requests will use non-personalized mode (`npa=1`).
- **Managing ad consent**: In regions where consent is required, go to Settings > Remove Ads > Ad Privacy Settings. Requests to access or delete advertising data processed by Google should be submitted directly to Google under its privacy policies (linked in §6.1).

Because the developer does not store any personal data, there are no user records held by the developer to access, correct, or delete.

## 10. Changes to this policy

If material changes are made to this policy, they will be noted in the App Store "What's New" release notes for the updated version, and the "Last updated" date at the top of this document will be revised.

## 11. Contact

- Email: [yjinchoi0623@gmail.com](mailto:yjinchoi0623@gmail.com)
- Support page: [Easy NAS Download Manager Support]({{ '/en/torrent/support/' | relative_url }})

---

## App-specific details — Easy NAS Download Manager

### A. What this app stores in the Keychain (common policy §3.1)

This app stores three types of items in its dedicated Keychain group, none of which ever leave your device:

1. **NAS connection profiles** (`nas.profiles.v2`): For each saved profile, this includes the profile name, server address or QuickConnect ID, port, HTTPS setting, DSM username and password, two-factor authentication preference and optional one-time password (OTP) seed, the trusted-device token and expiration issued by DSM, and your default and recently used destination folders.
2. **NAS certificate trust** (`certtrust.nas.v1`): Fingerprints of self-signed NAS certificates you have approved.
3. **Website certificate trust** (`certtrust.browser.v1`): Fingerprints of website certificates you have approved in the in-app browser. This store is completely isolated from the NAS certificate trust store in item 2.

In addition, the shared access group contains a single ad-free status entry shared across all three apps (common policy §3.1).

### B. Settings synced through iCloud (common policy §4)

This app syncs 6 preference keys via iCloud, all of which are general settings rather than credentials: appearance, default search engine, JavaScript enabled/disabled, pop-up blocking enabled/disabled, the UUID identifier of the active NAS profile (excluding its address, username, and password), and the default destination folder path string.

Bookmarks, cookies, diagnostic logs, download task lists, and items in the "Waiting to be added" queue are not synced.

### C. What this app connects to (common policy §6)

This app connects only to two types of user-selected destinations, along with Google for ads and Apple's App Store for in-app purchases as shared across all three apps (common policy §6.1, §6.2):

1. **Your configured Synology NAS**: Used to sign in, view your task list, and create, pause, resume, or delete tasks. If you connect using a QuickConnect ID, the app contacts Synology's QuickConnect service to resolve the server's address; this occurs only when QuickConnect is enabled.
2. **Websites you open in the in-app browser**: You enter the URLs yourself. The app does not preload any default websites or provide site directories or recommendations. Searches entered into the address bar are sent to the search engine selected in Settings (Google, DuckDuckGo, or Bing).

This app does not download media or content files (such as videos or music) to your device. The only file the app ever fetches directly is the `.torrent` metadata file (typically a few tens of kilobytes) to pass to your NAS, and only when a site requires a login that prevents your NAS from fetching the URL on its own. That metadata file is uploaded straight to your NAS without being retained or shared with any third party. All actual content downloads are carried out by Download Station on your NAS.

There is no developer-operated server.

### D. Permissions the app requests

This app requests two permissions:

- **Local Network access**: iOS prompts once when connecting to a NAS located on your local network (a private IP address). The app does not scan or browse your network for devices; it connects strictly to the address you entered in NAS settings.
- **App Tracking Transparency**: Common to all three apps, requested once after the ad-consent check. Allowing it enables personalized ads; otherwise, only non-personalized ads are requested (common policy §6.1). You can change this setting at any time in iOS Settings > Privacy & Security > Tracking.

The app does not request access to your photos, camera, microphone, location, contacts, notifications, health data, or calendar. None of these usage-description keys exist in the app's `Info.plist`, and the corresponding APIs are not called.

### E. Third-party libraries

This app does not link any third-party open-source libraries, as noted in the app under Settings > Open source licenses.

The only third-party SDK included is the Google Mobile Ads SDK (including the User Messaging Platform), which is shared across all three apps and used solely to display ads (see common policy §6.1). No analytics or crash-reporting SDKs are used.

### F. What you can delete inside the app (common policy §9)

| Data type | Location | What is removed |
|---|---|---|
| Web data | Settings > Browser > Clear web data | Browser cookies, cache, and active website logins (NAS profiles and bookmarks are kept). |
| Browser certificate trust | Settings > Browser > Reset browser certificate trust | Approved website certificate fingerprints (`certtrust.browser.v1`); NAS certificate trust is kept. |
| NAS profile | Settings > NAS > NAS profiles > [profile] > Delete this profile | The profile's server address, username, password, OTP seed, and trusted-device token. |
| Device trust | NAS connection settings > Security > Revoke trust for this device | The trusted-device token issued by DSM. |
| Diagnostic log (on-screen) | Settings > About > Diagnostics > Clear on-screen log | In-memory log entries (session log files on disk remain). |
| Ad consent | Settings > Remove Ads > Ad Privacy Settings (visible only in applicable regions) | Your Google ad-consent preferences (common policy §6.1). |

Uninstalling the app removes all of the data above, along with any `.torrent` files queued in "Waiting to be added". Keychain items follow the retention rules in common policy §3.1. Queued items can also be deleted individually, and older items expire automatically.

### G. When plain HTTP is used, and why (common policy §7)

Unencrypted HTTP connections occur in only two situations:

1. **Your NAS does not use HTTPS**: Home NAS devices typically run on a local network where Synology DSM defaults to plain HTTP on port 5000. If you have not enabled HTTPS on your NAS, the app connects over HTTP; if HTTPS is enabled, the app uses HTTPS and never downgrades the connection.
2. **A website you open in the in-app browser uses HTTP**: Because the built-in browser is a general-purpose web browser, it allows you to open websites that do not yet support HTTPS.

In both cases, the connection goes only to your own NAS at the address you provided or to a website you opened directly. No traffic is ever sent to the developer. Invalid or self-signed certificates are blocked unless you explicitly approve the host, and certificate trust records for your NAS and the browser are kept in separate Keychain stores as described in §A.

---

### H. Encryption and export compliance (common policy §7)

This app uses only the standard HTTPS (TLS) encryption built into the operating system. It qualifies for the standard encryption exemption under Category 5 Part 2 of the U.S. Export Administration Regulations and declares this in its App Store configuration (`ITSAppUsesNonExemptEncryption = false`).

---

*This document is available in English and Korean. In case of interpretive divergence, the
English version prevails.*
