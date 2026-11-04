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
**Last updated**: 2026-11-03 **Version**: 2.0

---

## 1. Summary

The developer does not collect any user data.

There is no developer-operated server, and the app has no network connection to the developer. Your data moves between your device and the servers or websites you choose to connect to. The developer has no access to it.

The app has no ads, and every feature is free. It does not track you and never asks for App Tracking Transparency (ATT) permission. The only in-app purchases are optional donations to support development, processed by Apple's App Store (§6.1).

## 2. Principles

- **No tracking.** The app contains no advertising, analytics or tracking SDKs and never requests App Tracking Transparency permission. The app's code never reads the advertising identifier (IDFA) or any other device identifier.
- **No analytics or crash-reporting SDKs.** The app does not include any third-party analytics or crash-reporting libraries.
- **No data is sent to the developer.** Usage history, device information, error reports, and purchase details are never transmitted to the developer.
- **No sale or sharing of user data.** Because the developer does not collect or hold any user data, nothing is sold or shared with third parties.

## 3. What the app stores on your device

### 3.1 iOS Keychain

The app uses the iOS Keychain to store sensitive data securely. The specific items stored vary by app and are detailed in the per-app section below.

All three apps apply the same security rules:

- Items are saved with the `kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly` accessibility setting.
  - `ThisDeviceOnly`: Items are not synced via iCloud Keychain and are excluded from device backups. They remain strictly on the device.
  - `AfterFirstUnlock`: The app can read these items while the screen is locked, provided the device has been unlocked at least once after a reboot.
- Credentials and certificate trust settings are isolated per app. Each app writes to its own dedicated Keychain access group, preventing one app from reading another app's passwords, accounts, or trusted certificates.
- iOS does not always remove Keychain items automatically when an app is deleted. If you want to ensure your saved credentials are completely removed, please delete them within the app before uninstalling it (§9).

### 3.2 App preferences (UserDefaults)

General preferences such as appearance (light/dark), sort order, and display options are stored in standard local storage (UserDefaults) and are accessible only to the app itself.

### 3.3 Files on the device

Files created by the app or saved by you remain on your device, either in the app's sandbox or, depending on the app, in a shared container used by this developer's apps (see the per-app section). The app reads file creation and modification timestamps within its own container to sort and display files and to rotate diagnostic logs.

## 4. What goes to iCloud — settings only

The app uses Apple's iCloud Key-Value Store to sync select preferences across your devices.

- Synced data: preference values such as feature toggles, selected options (e.g., appearance or search engine), numeric settings, default folder path strings, and the active profile identifier (UUID).
- Excluded data: passwords and other credentials, the contents of photos, videos, or documents, browsing history, bookmarks, and diagnostic logs.
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

The app makes network connections only to destinations that you configure or open yourself, as well as Apple's App Store for processing in-app purchases (donations, §6.1). User-configured destinations vary by app and are listed in the per-app section.

Across all three apps, there is no developer-operated server, and the app never sends requests to the developer.

### 6.1 In-app purchases (donations) — Apple App Store

- Every feature is free and there are no ads. In Settings > Support Development you can make one of three optional donations (Small Donation, Donation, Big Donation — consumable in-app purchases) to support development. A donation unlocks nothing; the screen simply says thank you.
- All payments are processed by Apple through the App Store. Neither the app nor the developer receives your payment details, credit card number, Apple ID, or any other personal information about the buyer.
- The app does not record donations anywhere — not on the device, in the Keychain, or in iCloud.

## 7. Security

- **Encrypted connections by default**: Whenever supported by the destination server, the app communicates over standard HTTPS (TLS).
- **Plain HTTP exceptions**: All three apps set `NSAllowsArbitraryLoads = true` so they can connect to destinations that only support unencrypted HTTP. The specific scenarios where plain HTTP is used, and the reasons for them, are explained in the per-app section. In all cases, the destination is either a website you opened directly or a personal server whose address you entered yourself; no traffic ever goes to the developer (§6).
- **Encryption and export compliance**: The app relies solely on standard encryption protocols (TLS, plus SSH and SMB 3 in applicable apps) and completes Apple's App Store export compliance declarations in accordance with U.S. export regulations. App-specific declarations are noted in the per-app section.
- **Credential storage**: Login credentials are stored in the iOS Keychain as outlined in §3.1.
- **Certificate verification**: When you explicitly choose to trust a host with a self-signed or untrusted certificate, the app saves that certificate's fingerprint and verifies it on subsequent connections. Certificate errors for unapproved hosts are blocked.

## 8. Children's privacy (COPPA)

The developer does not collect personal information from anyone, including children under the age of 13, and the app is not directed at children. The app has no ads and no tracking; all data remains on your device and the servers you connect to.

## 9. Your control and how to delete data

- **Uninstalling the app**: Deleting the app removes its local sandbox files and preferences. If the app uses a shared storage container with another app from this developer, files in that shared container remain on the device as long as any sibling app using it stays installed (see the per-app section). For Keychain retention details, see §3.1.
- **Clearing data within the app**: You can delete stored data directly from the app's Settings screen. Available deletion options and their menu locations are listed in the per-app section.
- **Disabling iCloud settings sync**: Open iOS Settings > [your name] > iCloud, and turn off iCloud access for this app.

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

The app connects only to the websites you open yourself, along with Apple's App Store for in-app purchases (donations), shared by all three apps. As a web browser, it connects to the URLs you enter in the address bar, the search engine you select in Settings, and the image URLs referenced on the pages you visit. Full details are listed in §D below.

### B. Shared policy §3.1 — what this app puts in the Keychain

This app stores only one item in its dedicated Keychain group:

| Item | Contents |
|---|---|
| `certtrust.browser.v1` | Certificate fingerprints of websites you have explicitly approved |

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
4. **In-app purchases (donations)**: Shared across all three apps, the app connects to Apple's App Store to process in-app purchases (see shared policy §6.1).

There is no developer-operated server and no network connection for analytics or crash reporting.

### E. Permissions — Photos (**add only**)

| Permission | Info.plist key | What it is actually for |
|---|---|---|
| Photos (add only) | `NSPhotoLibraryAddUsageDescription` | Requested only when you tap "Save to Photos" in the image viewer to add that single image to your photo library. The app never reads your photo library and contains no read-permission key. |

Downloaded images are saved to the app's Downloads folder (§H) by default and are added to the iOS Photos app only when you explicitly choose "Save to Photos" in the viewer. The app does not send notifications.

- **Permissions never requested**: photo library read access, notifications, camera, microphone, location, contacts, calendar, health data, local network access, or tracking (ATT).

As a general-purpose web browser, the app enables `NSAllowsArbitraryLoads` (App Transport Security exception) solely so that you can open websites that do not yet support HTTPS. It is not used for any developer server or private hardware. Any website whose TLS certificate fails validation remains blocked unless you explicitly approve that host, in which case its fingerprint is saved in the Keychain store described in §B.

Accordingly, the only scenario where unencrypted HTTP is used in this app (under shared policy §7) is when you visit an HTTP website yourself. Because no traffic is ever sent to the developer, no unencrypted traffic goes to the developer either.

### F. Third-party libraries — **none**

This app does not link any third-party open-source libraries and does not use CocoaPods. All app code is written for this project or relies on standard Apple system frameworks.

It also contains no advertising, analytics, or crash-reporting SDKs.

You can also view this information in the app under Settings > About > Open Source Licenses.

### G. Shared policy §9 — what you can delete in this app

- **Settings > Data**: Offers four options—Clear cache, Clear cookies (sign out), Reset saved tabs, and Clear Saved-Image Marks (which clears the green-outline URL history described in §C while keeping your saved image files). Each option prompts for confirmation and cannot be undone. Bookmarks are not affected by these actions and can be deleted individually on the Bookmarks screen.
- **Settings > Diagnostics > Diagnostic log**: Tap Clear to empty the on-screen log.
- **Saved images**: Delete files and folders directly on the app's Downloads screen, or from the "iPhone Folder" screen in Easy NAS Photo Viewer if that app is installed (§H).
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
