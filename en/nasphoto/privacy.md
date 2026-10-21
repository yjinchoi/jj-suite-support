---
layout: default
lang: en
title: "Privacy Policy — Easy NAS Photo Viewer"
permalink: /en/nasphoto/privacy/
alt: /nasphoto/privacy/
app: nasphoto
kind: privacy
description: "What information Easy NAS Photo Viewer handles, where it is stored and who it talks to."
---

# Privacy Policy

**Applies to**: Easy NAS Photo Viewer (iOS)
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
- Support page: [Easy NAS Photo Viewer Support]({{ '/en/nasphoto/support/' | relative_url }})

---

## App-specific details — Easy NAS Photo Viewer

### Keychain items in this app (common §3.1)

This app uses the Keychain service name `com.jjnasphoto.keychain` and stores credentials in its dedicated access group (`$(AppIdentifierPrefix)com.jjnasphoto.app`). These credentials are not shared with sibling apps.

Two types of items are stored exclusively for this app:

1. **Server profiles** (`nas.profiles.v2`): Stores connection details for each registered server. Synology NAS, SMB, and SFTP servers share this store.
   - Common fields: server type, address, port, username, password (SFTP can use a private key instead), folder settings (default folder and recent folders), and a profile identifier (UUID).
   - Synology NAS: QuickConnect ID and HTTPS preferences, two-factor authentication (TOTP) seed, and the trusted-device token and expiration issued by DSM.
   - SMB servers: share name and domain.
   - SFTP servers: starting path, authentication method (password or private key), the imported OpenSSH private key (Ed25519 or RSA) and its passphrase, and the server host-key fingerprint (`SHA256:…`) approved on first connection.
2. **NAS certificate trust fingerprints** (`certtrust.nas.v1`): Stores the fingerprint of any self-signed certificate you explicitly approve in an alert, which is verified on future connections.

As described in common §3.1, these items are stored for this device only; they do not sync via iCloud Keychain and are excluded from device backups. In addition, the shared access group holds one ad-free status entry common to all three apps (common §3.1).

### What goes to iCloud (common §4)

This app syncs 13 preference keys via the iCloud Key-Value Store:

- Synced keys: appearance (light/dark), grid column count, default upload folder path, NAS sort field, sort direction, folder view mode (grid/list), automatic renaming on filename conflict, active profile identifier (UUID), video skip interval (seconds), default playback engine, whether to show the playback engine picker, autoplay next video, and slideshow interval.
- Not synced: passwords and other credentials, the contents of photos, videos, or documents, video resume positions, last browsed folder, recent folder history, and diagnostic logs (the last browsed location and recent folders are device-specific states and are intentionally excluded).

The iCloud Key-Value Store container identifier is `$(TeamIdentifierPrefix)com.jjnasphoto.app`, which is isolated to this app.

### Who this app talks to (common §6)

This app connects to the servers you configure in server settings, which may be a Synology NAS, an SMB file server (such as a shared folder on Windows, macOS, or a NAS), or an SFTP server over SSH. In addition, it connects to Google for ads and Apple's App Store for in-app purchases, as shared across all three apps (common §6.1, §6.2).

- You enter the server address yourself (a local network IP, public domain or IP, or Synology QuickConnect ID) and choose the port and HTTPS setting.
- Only when you use a QuickConnect ID does the app query Synology's QuickConnect resolution service to resolve that ID into a connectable address.
- The app does not scan or discover devices on your network. It contains no Bonjour/mDNS browsing, subnet scanning, or automatic device discovery code.
- This app does not include a web browser and has no code path to open general websites.
- File uploads are supported only for Synology NAS servers. When you upload files from the iPhone Folder or select items from your photo library, the app writes the upload payload to a temporary local file and hands the transfer to the iOS background transfer service. This allows iOS to continue uploading to your NAS even if you lock the screen or switch apps. Temporary files are deleted once the transfer completes. SMB and SFTP servers are used only for browsing, downloading, and media playback.
- SFTP host-key pinning (Trust On First Use): The first time you connect to an SFTP server, the app displays the server's host-key fingerprint and connects only after you approve it. The fingerprint is saved to the server profile, and future connections are blocked if the server's key changes.
- Video playback from a Synology NAS uses unencrypted HTTP (explained below). Videos on an SMB server are streamed directly over SMB by the built-in VLC player, while videos on an SFTP server are read over SFTP by the app and piped to the built-in VLC player. URLs containing credentials are never passed to external apps.

### When unencrypted transfer is used, and why (common §7)

Unencrypted transfers occur in only three situations, and in all of them the destination is your own server at an address you entered:

1. **Your NAS does not use HTTPS**: Home NAS devices typically run on a local network where Synology DSM defaults to plain HTTP on port 5000. If you have not enabled HTTPS on your NAS, the app connects over HTTP. If HTTPS is enabled, the app uses HTTPS and never downgrades the connection.
2. **Video playback**: Media playback engines (MobileVLCKit, AVPlayer, and external VLC) each maintain their own network stack and cannot share the self-signed certificate trust stored by the app, causing HTTPS playback to fail silently. As a result, playback URLs use the NAS's HTTP port, matching the behavior of Synology's official DS file app.
3. **SMB servers**: The app uses SMB signing and authentication but does not enable SMB 3 transport encryption. File contents transferred over SMB are therefore unencrypted on the network, and SMB support is intended for trusted networks such as a home or office LAN.

SFTP connections are not affected by these exceptions; SFTP runs over SSH, encrypting both authentication and file contents in transit.

In all three cases, traffic goes solely to your own server and crosses the internet only if you have configured your server for remote access. No connection is ever made to the developer. This requirement is also noted in the Requirements section of the App Store description.

### Permissions this app requests

| Permission | Info.plist key | What it is actually for |
|---|---|---|
| Photos (add only) | `NSPhotoLibraryAddUsageDescription` | Used only when saving a photo you are viewing into the iPhone Photos app. The app never requests read access to your photo library and does not include a read-permission key. |
| Local Network | `NSLocalNetworkUsageDescription` | Used to connect to a NAS, SMB, or SFTP server on a private IP address (e.g., 192.168.x.x). iOS prompts once the first time a local network address is contacted. |
| App Tracking Transparency | `NSUserTrackingUsageDescription` | Common to all three apps, requested once after the ad-consent check. Allowing it enables personalized ads; otherwise, only non-personalized ads are requested (common §6.1). You can change this in iOS Settings > Privacy & Security > Tracking. |

No other permissions—such as location, contacts, microphone, camera, health, or notifications—are requested.

When you choose "Upload from Photo Library…" on a folder screen, the app opens the standard iOS photo picker (PHPicker). Because PHPicker runs as a separate system process, the app cannot browse your photo library and receives only the specific photos and videos you select, which requires no photo library read permission. Selected items are copied unmodified to a temporary local folder for upload to your NAS and deleted immediately afterward.

### Third-party libraries

This app uses the following open-source libraries along with the advertising SDK shared by all three apps:

- **MobileVLCKit 3.7.3** (VideoLAN, LGPL v2.1 or later): Decodes media in the "Built-in VLC" playback mode and streams videos from SMB servers.
- **AMSMB2 4.0.3** (including libsmb2, LGPL v2.1 or later): Used only when connecting to SMB servers.
- **SFTP networking stack**: Used only when connecting to SFTP servers, comprising Citadel 0.12.1 (MIT), swift-nio-ssh (Citadel fork), swift-nio, swift-asn1, swift-log, swift-atomics, swift-collections, swift-system (Apache 2.0), swift-crypto (Apache 2.0, including BoringSSL under OpenSSL / SSLeay / ISC licenses), and BigInt (MIT).
- **Google Mobile Ads SDK** (including the User Messaging Platform): Used solely to display ads (see common §6.1).

None of the open-source libraries include data collection, analytics, or advertising features. The two LGPL libraries (MobileVLCKit and AMSMB2) are linked as dynamic frameworks. Full license texts, copyright notices, and source repository links are available in the app under Settings > Open Source Licenses. No analytics or crash-reporting SDKs are included.

### Shared storage — the "iPhone Folder" shared with the Web Image app (common §3.3, §9)

This app's "iPhone Folder" uses a shared on-device container (`Files/` inside the App Group `group.com.jjsuite.shared`) alongside the developer's sibling app, Easy Web Image Collector.

- Files downloaded from your NAS, files received via the iOS share sheet, images saved by Easy Web Image Collector, and folders you create are all stored in this single shared folder and appear in both apps.
- Both apps can read and delete files in this folder. Files leave the device only when you manually upload them to your NAS.
- This shared container does not appear under "On My iPhone" in the iOS Files app. Any files placed into the app's folder via Finder or the Files app, as well as files stored in legacy app folders (`Documents/` or earlier subfolders like Received, Downloads, and Web Images), are automatically migrated to this shared folder on the next launch (excluding diagnostic logs).
- If you uninstall this app while Easy Web Image Collector remains on your device, the files in the shared folder are retained. They are deleted by iOS once all apps sharing the container have been uninstalled.

### What you can delete inside the app (common §9)

Under Settings > Data, you can clear three types of cached data:

- **Clear image cache**: Removes in-memory thumbnails (which are also cleared automatically when the app closes).
- **Clear original image cache**: Removes full-resolution cached bitmaps generated by the image viewer.
- **Clear resume history**: Deletes saved playback positions for all videos without deleting the video files themselves.

Other data can be managed as follows:

- **Files in the iPhone Folder**: Select and delete items directly on the folder screen.
- **Server profiles and credentials**: Open Manage profiles on the home screen (the NAS profile list) and swipe left on a profile to delete it. This removes the server address, account credentials, and recent folder history from the Keychain, without affecting any files on your server.
- **Ad consent**: In regions where consent is required, update your preference under Settings > Remove Ads > Ad Privacy Settings.
- **Diagnostic logs**: Go to Settings > Diagnostics > Diagnostic log to view logs, export the current session file via the share sheet, or clear the on-screen log. Only the 10 most recent session files are kept on disk; older ones are deleted automatically.

### Encryption and export compliance (common §7)

In addition to standard HTTPS (TLS), this app includes SSH encryption for SFTP and SMB 3 encryption. Accordingly, rather than claiming the standard encryption exemption key, export compliance is fulfilled by submitting export compliance documentation in App Store Connect (including the French encryption declaration). All encryption is used strictly for connections to servers that you own and configure yourself.

---

*This document is available in English and Korean. In case of interpretive divergence, the
English version prevails.*
