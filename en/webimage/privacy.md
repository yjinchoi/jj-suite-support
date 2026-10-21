---
layout: default
lang: en
title: "Privacy Policy — Easy Web Image Collector"
permalink: /en/webimage/privacy/
alt: /webimage/privacy/
app: webimage
kind: privacy
description: "What information Easy Web Image Collector handles, where it is stored and who it talks to."
---

# Privacy Policy

**Applies to**: Easy Web Image Collector (iOS)
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
- Support page: [Easy Web Image Collector Support]({{ '/en/webimage/support/' | relative_url }})

---

## App-specific details — Easy Web Image Collector

### A. This app connects to no storage server and to no developer server

This app does not include any NAS features. It does not connect to a Synology NAS or any other external storage server, and it has no login, account, or profile settings. Because there is no developer-operated server either, the app never sends requests to the developer and works right after installation without any setup.

The app connects only to the websites you open yourself, along with the two external services shared by all three apps: Google for ads and Apple's App Store for ad-free purchases. As a web browser, it connects to the URLs you enter in the address bar, the search engine you select in Settings, and the image URLs referenced on the pages you visit. Full details are listed in §D below.

### B. Shared policy §3.1 — what this app puts in the Keychain

This app stores only one item in its dedicated Keychain group:

| Item | Contents |
|---|---|
| `certtrust.browser.v1` | Certificate fingerprints of websites you have explicitly approved |

In addition, the shared access group holds one ad-free status entry common to all three apps (shared policy §3.1).

Because this app has no login functionality, no passwords, account credentials, or authentication tokens are stored.

If a website prompts for HTTP authentication (a username and password dialog), the credentials you enter are held in memory for that active session only and are never saved to the Keychain. If you quit and relaunch the app, the website will prompt you again.

### C. Shared policy §4 — the **8** settings that sync via iCloud

This app syncs 8 preference keys via iCloud: appearance (system, light, or dark), default search engine (Google, DuckDuckGo, or Bing), JavaScript enabled/disabled, pop-up blocking enabled/disabled, Instant Save enabled/disabled, whether the Instant Save introduction has been viewed, the relative path string of the default download folder, and automatic file numbering on filename collisions.

All eight items are general preferences. Saved image files, browsing history, open tabs, bookmarks, the saved-image URL record (described below), and diagnostic logs are not synced. The seventh item is only the folder path string, not the files inside it. Downloads view mode, column count, and slideshow interval remain device-specific and do not sync.

To highlight already-saved images with a green outline on web pages, the app keeps a local list of image URLs saved via Instant Save (up to the 5,000 most recent URLs). This list stays strictly on your device, is never synced via iCloud or transmitted externally, and is not visible in the iOS Files app. You can clear it at any time under Settings > Data > Clear Saved-Image Marks without deleting your saved image files.

### D. Shared policy §6 — who the app talks to

This app communicates primarily with websites you open directly, limited to the following four cases:

1. **Web addresses you enter**: The app connects to the URL typed into the address bar.
2. **Search queries you enter**: Queries typed into the address bar are sent to the search engine selected in Settings (Google, DuckDuckGo, or Bing; Google is the default).
3. **Image downloads**: When you save an image from a page opened via (1) or (2), the app downloads the image file directly from that image's URL. It does not send image requests to any other destination.
4. **Ads and ad-free purchases**: Shared across all three apps, the app connects to Google for serving ads and Apple's App Store for processing in-app purchases (see shared policy §6.1 and §6.2).

There is no developer-operated server and no network connection for analytics or crash reporting.

### E. Permissions — Photos (**add only**) and App Tracking Transparency

| Permission | Info.plist key | What it is actually for |
|---|---|---|
| Photos (add only) | `NSPhotoLibraryAddUsageDescription` | Requested only when you tap "Save to Photos" in the image viewer to add that single image to your photo library. The app never reads your photo library and contains no read-permission key. |
| App Tracking Transparency | `NSUserTrackingUsageDescription` | Common to all three apps, requested once after the ad-consent check. Allowing it enables personalized ads; otherwise, only non-personalized ads are requested (common §6.1). You can change this in iOS Settings > Privacy & Security > Tracking. |

Downloaded images are saved to the app's Downloads folder (§H) by default and are added to the iOS Photos app only when you explicitly choose "Save to Photos" in the viewer. The app does not send notifications.

- **Permissions never requested**: photo library read access, notifications, camera, microphone, location, contacts, calendar, health data, or local network access.

As a general-purpose web browser, the app enables `NSAllowsArbitraryLoads` (App Transport Security exception) solely so that you can open websites that do not yet support HTTPS. It is not used for any developer server or private hardware. Any website whose TLS certificate fails validation remains blocked unless you explicitly approve that host, in which case its fingerprint is saved in the Keychain store described in §B.

Accordingly, the only scenario where unencrypted HTTP is used in this app (under shared policy §7) is when you visit an HTTP website yourself. Because no traffic is ever sent to the developer, no unencrypted traffic goes to the developer either.

### F. Third-party libraries — **no** open source, one advertising SDK

This app does not link any third-party open-source libraries and does not use CocoaPods. All app code is written for this project or relies on standard Apple system frameworks.

The only included third-party SDK is the Google Mobile Ads SDK (including the User Messaging Platform for consent management), which is used solely to display ads (see shared policy §6.1). No analytics or crash-reporting SDKs are included.

You can also view this information in the app under Settings > About > Open Source Licenses.

### G. Shared policy §9 — what you can delete in this app

- **Settings > Data**: Offers four options—Clear cache, Clear cookies (sign out), Reset saved tabs, and Clear Saved-Image Marks (which clears the green-outline URL history described in §C while keeping your saved image files). Each option prompts for confirmation and cannot be undone. Bookmarks are not affected by these actions and can be deleted individually on the Bookmarks screen.
- **Settings > Diagnostics > Diagnostic log**: Tap Clear to empty the on-screen log.
- **Saved images**: Delete files and folders directly on the app's Downloads screen, or from the "iPhone Folder" screen in Easy NAS Photo Viewer if that app is installed (§H).
- **Ad consent**: In regions where consent is required, manage your preference under Settings > Remove Ads > Ad Privacy Settings.
- **Uninstalling the app**: Deleting the app removes all local data above, with two exceptions: saved images in the shared storage container remain on the device as long as Easy NAS Photo Viewer stays installed (§H), and Keychain items follow shared policy §3.1. The 8 synced preferences in §C may remain in iCloud for your other devices signed in with the same Apple ID.

### H. Where saved images live — storage shared with the developer's other app

Saved images are stored locally in a shared container (`Files/` inside the App Group `group.com.jjsuite.shared`), which is a single folder shared with the developer's sibling app, Easy NAS Photo Viewer.

- If Easy NAS Photo Viewer is installed on the same device, it displays this folder as its "iPhone Folder". Files downloaded or received via the share sheet in that app are stored in the same folder and appear on this app's Downloads screen as well. Easy NAS Photo Viewer can open and delete these files, and can upload them to your personal server when you explicitly choose to do so. Files never leave your device unless you manually upload them from that app.
- This shared folder does not appear under "On My iPhone" in the iOS Files app; you can export files using the Share button on the Downloads screen.
- Any files saved in the legacy app folder (`Documents/Downloads/`) by an earlier version are automatically moved to this shared container when you first launch the updated app.
- Uninstalling this app leaves the files in place if Easy NAS Photo Viewer is still installed; iOS removes the shared folder once all apps using it have been uninstalled.

---

### I. Shared policy §7 — encryption and export compliance

This app uses only the standard HTTPS (TLS) encryption built into the operating system. It qualifies for the standard encryption exemption under Category 5 Part 2 of the U.S. Export Administration Regulations and declares this in its App Store configuration (`ITSAppUsesNonExemptEncryption = false`).

---

*This document is available in English and Korean. In case of interpretive divergence, the
English version prevails.*
