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
**Last updated**: 2026-10-19 **Version**: 1.1

---

## 1. Summary

**The developer collects no user data.**

There is no developer-operated server, and the app has no network route to the developer.
Your data moves between **your device** and **servers you own and configured yourself**.
The developer cannot see any of it.

The app is free and shows **Google AdMob ads**. To load them, Google's advertising SDK inside the
app sends some device data **directly to Google** (§6.1). The app asks once for iOS
**App Tracking Transparency (ATT)** permission. **Only if you allow it** is the advertising identifier
(IDFA) provided to Google for personalized ads; otherwise only **non-personalized ads** are requested
(§6.1). The **in-app
purchase** that removes ads is handled by Apple's App Store (§6.2).

## 2. Principles

- **Tracking only if you allow it.** The app asks once for App Tracking Transparency permission. If
  you **allow** it, the advertising SDK uses the advertising identifier (IDFA) to request personalized
  ads, which counts as **tracking** under Apple's definition. If you do **not** (denied, not yet decided,
  or restricted), the IDFA is not provided and every ad request is marked **non-personalized**
  (`npa=1`). The app's own code reads neither the advertising identifier nor any device identifier.
  You can change your choice at any time in **iOS Settings › Privacy & Security › Tracking**.
- **No analytics or crash-reporting SDK.** No third-party analytics SDK and no third-party
  crash-reporting library is bundled. The one advertising SDK bundled is the **Google Mobile Ads
  SDK** (including the User Messaging Platform for consent); the data it handles is described in §6.1.
- **Nothing reaches the developer.** No usage records, device information, error reports, or
  purchase information are transmitted to the developer.
- **The developer neither sells nor shares user data.** The developer holds none to begin with.
  Data the advertising SDK sends directly to Google is covered in §6.1.

## 3. What the app stores on your device

### 3.1 iOS Keychain

The app uses the iOS Keychain. What exactly is stored differs per app and is listed in the
**per-app section** that follows this document.

The protection applied is the same in all three apps:

- Accessibility attribute: **`kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly`**.
  - `ThisDeviceOnly` — these items are **not synchronized through iCloud Keychain** and are
    **not included in device backups**. They never leave the device.
  - `AfterFirstUnlock` — readable by the app while the screen is locked, but only after the
    first unlock following a reboot.
- **Credentials and certificate trust live in a per-app store.** Each app writes to its own
  Keychain access group, so no app can read another app's passwords, accounts, or certificate trust.
- **One exception: the ad-free purchase record.** So that buying ad removal in one app also removes
  ads from the other two on the same device, the three apps share one access group
  (`com.jjsuite.shared`) in which each app keeps a single item. It holds **only the ad-free status
  (none, an expiry date, or lifetime) and when it was last updated** — no payment details, no
  Apple ID, no receipt. This sharing happens only between this developer's apps on the same device.
- iOS does not guarantee that deleting an app deletes its Keychain items. To be sure stored
  credentials are gone, clear them inside the app **before** deleting it (§9). The ad-free record
  stays after an app is deleted and keeps applying to the other two apps.

### 3.2 App preferences (UserDefaults)

Settings such as appearance (light/dark), list sort order, and display options are stored in
the device's standard preferences store. Only the app itself can read them. The ad-consent state
(§6.1) is also recorded there, by Google's consent SDK.

### 3.3 Files on the device

Files the app creates, or that you save into it, stay **on the device** — in the app sandbox or,
depending on the app, in a storage area shared between this developer's apps (described in the
**per-app section**). The app reads **file timestamps within its own container** to sort and
display files and to rotate diagnostic log files.

## 4. What goes to iCloud — settings only

The app uses Apple's **iCloud Key-Value Store** to synchronize **some settings** with your own
other devices.

- What syncs: **settings values** — toggles, enumerated choices (e.g. appearance, search
  engine), numeric values, default folder path strings, and the active profile identifier (a UUID).
- What does **not** sync: **any credential, including passwords**; the contents of photos,
  videos, or documents; browsing history; bookmarks; diagnostic logs; the ad-free purchase
  record; the ad-consent state.
- **The store is per-app.** The three apps cannot overwrite each other's values.
- This synchronization is **operated by Apple**. The data lives in your iCloud account and the
  **developer has no access to it.**
- There is no in-app toggle for it. Turning iCloud off for the app in iOS Settings stops it.

The exact list and count of synchronized keys differs per app and is given in the
**per-app section**.

## 5. Diagnostic log

The app keeps a diagnostic log **on the device** to help with troubleshooting.

- Location: `Documents/diagnostics/` inside the app container (one text file per session,
  the 10 most recent kept).
- The log is **never transmitted automatically.** It leaves the device only when you
  explicitly export it through the share sheet in Settings.
- It may contain: timestamps and outcomes of operations, error messages, the address of a
  server the app contacted and the request path, and the target of a failed request. One line
  at session start records the device model, iOS version, and app version — values needed to
  reproduce a problem, not an identifier unique to your device.
- It does **not** contain passwords or two-factor seeds. Server session keys are masked
  before being written.

If you attach a diagnostic log to a support request, be aware that the above travels with it.
You are welcome to write in without attaching one.

## 6. Who the app talks to

The app's network connections go to destinations **you configured or opened yourself**, and to
two services: **Google**, for ads (§6.1), and **Apple's App Store**, for the ad-free purchase (§6.2).
The destinations you configure differ per app and are listed in the **per-app section**.

What is true for all three: **no developer-operated server exists.** The app sends the
developer no requests of any kind.

### 6.1 Ads — Google AdMob

- **When ads appear**: once when the app starts fresh (an app-open ad — skipped for that launch if
  it is not ready within 4 seconds), and once for every 30 minutes of accumulated on-screen use (an
  interstitial — only at a moment when you are not interacting, such as after a screen change). No
  ad is shown once you have bought ad removal, or while another window such as first-run guidance,
  a sheet, or an alert is open.
- **Tracking permission (ATT) and personalized ads**: after ad consent (below), while the app is on
  screen, it shows iOS's tracking-permission prompt **once**.
  - If you **allow** it, the advertising identifier (IDFA) is provided to Google and you may see
    **personalized ads** based on your interests and your activity in other companies' apps and
    websites. Under Apple's definition this is **tracking**.
  - If you do **not** allow it (or it is restricted on the device), the IDFA is not provided and every
    ad request is marked non-personalized (`npa=1`).
  - Either way the app works the same and shows the same number of ads. Change your choice at any
    time with this app's switch in **iOS Settings › Privacy & Security › Tracking**.
- **Consent**: at start-up the app uses Google's User Messaging Platform to check whether consent
  is required, and in the European Economic Area, the UK and similar regions it shows Google's
  consent form **before** requesting any ad. Without confirmed consent, no ad is requested. You can
  change your choice at any time under **Settings → Remove Ads → Ad Privacy Settings** (the row
  appears only in regions where consent is required).
- **Data Google may process** (per Google's published AdMob disclosure): device identifiers,
  advertising data (which ads you saw and tapped), product interaction (app launches, taps),
  coarse location (estimated from the IP address), and diagnostics (performance and errors). The
  purposes are **advertising** — serving and measuring ads and preventing fraud — and Google's analytics
  and ad-performance measurement. Of these, **device identifiers may be used for tracking** (the IDFA,
  if you allowed tracking), and coarse location, advertising data, product interaction and device
  identifiers may be linked to you on Google's side. If you do not allow tracking, the IDFA is not provided.
- The Google SDK inside the app sends this data **directly to Google's servers**. It does not pass
  through any developer server, and the developer receives no individual user data — only
  **aggregate reports** such as impressions and earnings in AdMob.
- Tapping an ad opens the advertiser's website or App Store page; what happens there is governed by
  that site's policy.
- Google's processing is governed by Google's policies:
  [Google Privacy Policy](https://policies.google.com/privacy) ·
  [How Google uses information from sites or apps that use its services](https://policies.google.com/technologies/partner-sites).

### 6.2 Ad-free purchase — Apple App Store

- The app sells three ad-removal products: **1 month** and **1 year** (non-renewing — never charged
  automatically) and **lifetime** (a one-time purchase).
- Payment is **processed by Apple on the App Store**. Neither the app nor the developer receives
  payment details such as card numbers, or your Apple ID. No information identifying the buyer is
  passed to the developer.
- The app uses Apple's StoreKit to read this app's purchase history on the device (which product
  was bought when, and whether it was refunded), calculates the ad-free period, and stores **only
  the result (status and expiry date)** in the shared Keychain item described in §3.1.
- **Restore Purchases** syncs with the App Store to fetch the purchase history again.

## 7. Security

- **Encrypted connections are preferred.** Where the other end supports it, the app talks to
  servers over standard HTTPS (TLS).
- **Plain HTTP is not blocked, because some cases need it.** All three apps declare
  `NSAllowsArbitraryLoads = true`, so a destination that offers only HTTP is reached in the
  clear. Which cases those are, and why, is stated in the **per-app section**. In every case
  the destination is a website you opened yourself or a server you own and addressed yourself;
  no connection goes to the developer (§6).
- The app qualifies for the standard-encryption exemption under Category 5 Part 2 of the U.S.
  Export Administration Regulations and declares this in its app information
  (`ITSAppUsesNonExemptEncryption = false`).
- Credentials are held in the iOS Keychain as described in §3.1.
- For hosts you explicitly choose to trust, the app stores that certificate's fingerprint and
  checks it on later connections. Certificate errors for hosts you have not approved are not
  bypassed.

## 8. Children's privacy (COPPA)

The developer collects no personal information from anyone, children under 13 included. The app
is not directed at children. Personalized ads are requested only if you allow tracking; otherwise only
non-personalized ads are requested. The data the advertising
SDK sends to Google is described in §6.1; everything else stays on your device and on servers you own.

## 9. Your control and how to delete data

- **Delete the app** — removes that app's local data: files in its sandbox and its settings. For an
  app that uses a storage area shared between this developer's apps, files there remain as long as
  any app using that area is still installed (see the **per-app section**). For Keychain items, see §3.1.
- **Delete from within the app** — the Settings screen lets you clear stored data. Where those
  controls live differs per app; what can be cleared is listed in the **per-app section**.
- **Turn off settings sync** — iOS Settings → [your name] → iCloud → turn iCloud off for this app.
- **Change tracking permission** — turn off this app's switch in iOS Settings › Privacy & Security ›
  Tracking. Later ad requests then become non-personalized (`npa=1`).
- **Change ad consent** — Settings → Remove Ads → Ad Privacy Settings (in regions where consent is
  required). Requests to access or delete advertising data Google has processed go to Google, under
  Google's policies (links in §6.1).

Because the developer holds no user data, there is nothing to request access to, correct, or
erase from the developer.

## 10. Changes to this policy

Material changes will be stated in the App Store "What's New" for the new version, and the
"Last updated" date above will be revised.

## 11. Contact

- Email: [yjinchoi0623@gmail.com](mailto:yjinchoi0623@gmail.com)
- Support page: [Easy NAS Photo Viewer Support]({{ '/en/nasphoto/support/' | relative_url }})

---

## App-specific details — Easy NAS Photo Viewer

### Keychain items in this app (common §3.1)

The Keychain service name is `com.jjnasphoto.keychain`, and credentials are stored in this app's
own access group `$(AppIdentifierPrefix)com.jjnasphoto.app`. They are not shared with the sibling apps.

Two things are stored for this app alone:

1. **Server profiles** (`nas.profiles.v2`) — for each registered server. Synology NAS and SMB
   servers use the same store.
   - All servers: server type, address, port, account name, **password**, folder settings
     (default folder, recent folders), and a profile identifier (UUID).
   - Synology NAS: whether a QuickConnect ID and HTTPS are used, the two-factor (TOTP) seed, and the
     trusted-device token issued by DSM with its expiry.
   - SMB servers: share name and domain.
2. **NAS certificate trust fingerprints** (`certtrust.nas.v1`) — the fingerprint of a self-signed
   certificate the user explicitly approved in an alert, checked against on later connections.

As stated in common §3.1 these items are stored **device-only**: they do not sync through
iCloud Keychain and are not included in device backups. Separately, the **ad-free status item**
common to all three apps sits in the shared group (common §3.1).

### What goes to iCloud (common §4)

This app syncs **13** preference keys through the iCloud Key-Value store:

appearance (light/dark), grid column count, default upload folder path, NAS sort field,
sort direction, folder view mode (grid/list), auto-rename-on-conflict, active profile
identifier (UUID), video skip seconds, default playback engine, whether the playback picker is
shown, autoplay-next, and the slideshow interval.

**Not synced**: any credential including passwords, the contents of photos, videos or documents,
resume positions, the last location you were browsing, the recent-folder list, and diagnostic logs.
(The last location and recent folders are per-device state and were deliberately left out.)

The KVS container identifier is `$(TeamIdentifierPrefix)com.jjnasphoto.app`, private to this app.

### Who this app talks to (common §6)

**The servers whose addresses the user typed into server settings**, of two kinds: a **Synology NAS**
and an **SMB file server** (a shared folder on Windows, macOS, or a NAS). On top of that come the ads
(Google) and the ad-free purchase (Apple App Store) common to all three apps (common §6.1, §6.2).

- The address is entered by the user — a LAN address, a public domain or IP, or (for Synology) a
  QuickConnect ID. The port and whether to use HTTPS are the user's choice too.
- When, and only when, a QuickConnect ID is used, the app queries **Synology's QuickConnect
  resolution service** to turn that ID into a reachable address.
- **No discovery, no scanning.** There is no Bonjour/mDNS browsing, no subnet scan and no device
  discovery code in the app.
- **There is no web browser in this app.** No code path opens an arbitrary website.
- **Uploads go only to a Synology NAS.** When you upload files from an iPhone folder, or items picked
  from your photo library, the app writes the request body to a temporary file on the device and hands
  it to iOS **background transfer**, so iOS keeps sending it **to the same NAS** even if you lock the
  screen or switch apps. The temporary files are deleted when the transfer ends. SMB servers are used
  only for browsing, downloading and playback.
- Video playback from a Synology NAS uses plain HTTP (below). Videos on an SMB server are read by the
  built-in VLC directly from that server over SMB; no address containing credentials is passed to
  another app.

### When unencrypted transfer is used, and why (common §7)

There are **only three cases**, and in all of them the other end is **the user's own server, at an
address the user typed in.**

1. **The NAS does not offer HTTPS.** A home NAS usually sits on the LAN and DSM's default is
   plain HTTP on port 5000. If the user has not enabled HTTPS on the NAS, the connection is in
   the clear. If they have, the app uses HTTPS — it never downgrades one that works.
2. **Video playback.** The playback engines (MobileVLCKit, AVPlayer, external VLC) each use
   their own network stack and cannot share the self-signed certificate trust the app has
   stored, so the HTTPS leg fails silently. Playback URLs are therefore built against the same
   NAS's HTTP port, exactly as Synology's own DS file client does.
3. **SMB servers.** The app does not turn on SMB 3 transport encryption; it uses signing and
   authentication only. **File contents exchanged over SMB are therefore not encrypted on the
   network.** It is meant for a trusted network such as a home or office LAN.

In every case the destination is a single machine the user owns, and traffic crosses the
internet only if the user has exposed that server themselves. No connection goes to the developer
in any case. This premise is also stated in the Requirements section of the App Store description.

### Permissions this app requests

| Permission | Info.plist key | What it is actually for |
|---|---|---|
| Photos — **add only** | `NSPhotoLibraryAddUsageDescription` | Saving a photo you are viewing into the iPhone Photos app. **Read access to the photo library is never requested** — there is no read-permission key in the app |
| Local Network | `NSLocalNetworkUsageDescription` | Reaching a NAS or SMB server on a private IP address (e.g. 192.168.x.x). iOS asks once, the first time a private address is contacted |
| App Tracking Transparency | `NSUserTrackingUsageDescription` | Common to all three apps — asked once after ad consent. Allow it for personalized ads; otherwise ads are non-personalized (common §6.1). Change it in iOS Settings › Privacy & Security › Tracking |

That is the complete list. The app does not request location, contacts, microphone, camera,
health or notification permissions.

**Uploading from your photo library — no permission, only what you pick.** "Upload from Photo
Library…" on a folder screen opens iOS's photo picker (PHPicker). The picker is a **system screen
separate from the app**: the app cannot see your library, and receives **only the photos and videos
you pick**, which is why no read permission is requested. Picked items are copied unchanged into a
temporary folder on the device, uploaded to your NAS, and the temporary copies are deleted.

### Third-party libraries

Two open-source libraries, plus the advertising SDK common to all three apps:

- **MobileVLCKit 3.7.3** (VideoLAN, LGPL v2.1 or later) — decodes media in the "Built-in VLC"
  playback mode and reads videos from SMB servers.
- **AMSMB2 4.0.3** (with libsmb2, LGPL v2.1 or later) — active only when connecting to an SMB server.
- **Google Mobile Ads SDK** (with the User Messaging Platform) — for showing ads only; see common **§6.1**.

The two open-source libraries have no network-collection, analytics or advertising functionality.
They are linked as dynamic frameworks, and their licences, copyrights and source repository links
are shown in-app under **Settings → Open Source Licences**.

There are no analytics SDKs or crash-reporting libraries.

### Shared storage — the "iPhone folders" shared with the Web Image app (common §3.3, §9)

This app's "iPhone folders" are a **shared storage area** on the device (`Files/` inside the App
Group `group.com.jjsuite.shared`), used together with the developer's **Easy Web Image Collector**.

- Files downloaded from the NAS ("Downloads"), files received through another app's share sheet
  ("Received"), and folders you create live here. Images saved by Easy Web Image Collector appear
  in the "Web Images" folder.
- Both apps can **read and delete** files in this area — Easy Web Image Collector works only with the
  "Web Images" folder on screen. Files leave the device only when you upload them to your own NAS.
- This area is **not visible under "On My iPhone" in the Files app.** Files you put into this app's
  folder through the Files app or Finder, and files an earlier version kept in the app's own folder
  (`Documents/`), are moved into this area on the next launch (diagnostic logs excepted).
- Deleting this app leaves these files in place while Easy Web Image Collector remains installed;
  they are removed when every app using the area has been deleted.

### What you can delete inside the app (common §9)

**Settings → Data** offers four actions:

- **Clear image cache** — in-memory thumbnails, which are discarded when the app quits anyway.
- **Clear original image cache** — the full-size bitmaps the viewer built.
- **Clear resume history** — every record of how far you watched. Video files are not deleted.
- **Empty Received folder** — **deletes from the device** the files other apps shared into this
  app. This cannot be undone, so the size is shown and confirmation is required first.

**Files in the iPhone folders** are deleted by selecting them on the folder screen (shared storage above).

**To delete a server profile and its credentials**, open **Manage profiles** on the first screen
(the NAS profiles list) and swipe that row away. Deleting the profile removes its address, account
and recent-folder history from the Keychain with it. Nothing on the server itself is deleted.

**Ad consent** is changed under Settings → Remove Ads → Ad Privacy Settings (where consent is required).

**Diagnostic logs** can be viewed under Settings → Diagnostics → Diagnostic log, where the current
session file can be exported through the share sheet and the on-screen records can be cleared.
Only the ten most recent session files are kept; older ones are removed automatically.

---

*This document is available in English and Korean. In case of interpretive divergence, the
English version prevails.*
