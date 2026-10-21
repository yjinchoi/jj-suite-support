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

- **When ads appear**: only while you wait for something the app is doing — for example connecting
  to a server, transferring files, or adding a task. A 300×250 banner labelled "Ad" appears inside the
  progress window for at least 2 seconds. There is **no ad at launch and no ad on a timer**, and none in
  the first 5 seconds after the app starts. No ad is shown once you have bought ad removal, before ad
  consent is settled, or when no ad has been loaded — the progress window then simply shows progress.
- **Tracking permission (ATT) and personalized ads**: on the **first launch**, after the ad-consent check
  (below), while the app is on screen, it shows iOS's tracking-permission prompt **once** and never again.
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
- The app uses only standard encryption (such as TLS, and in some apps SSH and SMB 3) and answers
  export-compliance questions in its App Store information as U.S. export rules and Apple require. How
  each app answers is stated in the **per-app section**.
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
- Support page: [Easy Web Image Collector Support]({{ '/en/webimage/support/' | relative_url }})

---

## App-specific details — Easy Web Image Collector

### A. This app connects to no storage server and to no developer server

**There is no NAS feature in this app.** It does not connect to a Synology NAS or to any
other storage server, and it has no login, account or profile settings. There is no
developer-operated server either — the app sends not one request to the developer. That is
why there is nothing to set up: install it, open it, and it works.

**The app connects to the websites you opened yourself**, plus the two services common to all
three apps: **ads (Google)** and the **ad-free purchase (Apple App Store)**. It is a web browser,
so of course it makes website connections: the address you typed, the search engine you chose in
Settings, and the image files that page points to. **§D** below lists them exactly.

### B. Shared policy §3.1 — what this app puts in the Keychain

**Exactly one item of its own.**

| Item | Contents |
|---|---|
| `certtrust.browser.v1` | Certificate fingerprints of websites **you approved yourself** |

In addition there is the **ad-free status item** common to all three apps (shared policy §3.1),
kept in the shared group.

No passwords, accounts or tokens are stored, because there is nothing to store — this app
has no sign-in screen.

If a site asks for HTTP authentication (a username/password dialog), what you type is kept
**for that running session only** and is never written to the Keychain. Relaunch the app and
the site asks again.

### C. Shared policy §4 — the **8** settings that sync via iCloud

Appearance; search engine (Google / DuckDuckGo / Bing); JavaScript on/off; pop-up blocking;
Instant Save on/off; whether the Instant Save intro has been seen; the **relative path
string** of the default download folder; whether to auto-number files on a name collision.

**All eight are preferences.** Image files, addresses you visited, open tabs, bookmarks, the
saved-image record (below) and diagnostic logs do not sync. Item seven is the folder's
*name*, not what is inside it. The Downloads view mode, column count and slideshow interval are
kept per device and do not sync.

**Saved-image record — kept on the device only.** To draw a green outline around pictures
you have already saved, the app remembers the **addresses (URLs) of the images** you saved
with Instant Save, in a file on the device (the most recent 5,000). This list is never sent
anywhere, never synced through iCloud, and not visible in the Files app. Empty it at any
time with **Settings → Data → Clear Saved-Image Marks**; your saved files stay.

### D. Shared policy §6 — who the app talks to

**Mainly websites you opened yourself**, in these cases only:

1. An address you typed — the app goes to that site.
2. A search term you typed — the app goes to the search engine chosen in Settings
   (Google, DuckDuckGo or Bing; Google by default).
3. Saving an image — the app fetches the image file you tapped on the page opened in (1)
   or (2), from that image's own address. **It sends no image request anywhere else.**
4. Ads and the ad-free purchase — common to all three apps. The app connects to Google (ads) and
   Apple's App Store (purchase), as described in shared policy **§6.1 and §6.2**.

There is no developer-operated server, and no connection for analytics or crash reporting.

### E. Permissions — Photos (**add only**) and App Tracking Transparency

| Permission | Info.plist key | What it is actually for |
|---|---|---|
| Photos — **add only** | `NSPhotoLibraryAddUsageDescription` | Asked only when you tap **Save to Photos** in the image viewer; that one image is added to your photo library. **The photo library is never read** — there is no read-permission key |
| App Tracking Transparency | `NSUserTrackingUsageDescription` | Common to all three apps — asked once after ad consent. Allow it for personalized ads; otherwise ads are non-personalized (common §6.1). Change it in iOS Settings › Privacy & Security › Tracking |

Saved images go to the app's Downloads folder (§H) by default; something goes into Photos only
when you choose it in the viewer. The app sends no notifications.

- **Never requested**: photo library read access, notifications, camera, microphone, location,
  contacts, calendar, health, local network.

**About the arbitrary-loads exception (ATS)** — the app sets `NSAllowsArbitraryLoads` for
one reason: it is a general-purpose browser, you may open any site, and some sites still do
not use HTTPS. It is not there for a developer server or private hardware. A certificate
that fails validation stays **blocked** until you explicitly approve that host, and an
approval is stored as the fingerprint described in §B.

Where the shared policy §7 speaks of "cases that need plain HTTP", this app has exactly
**one**: an HTTP website you opened yourself. No plain-text traffic goes to the developer,
because no traffic goes to the developer at all.

### F. Third-party libraries — **no** open source, one advertising SDK

This app links **no** third-party open-source library. It does not use CocoaPods; the code
is either written for this project or provided by Apple's system frameworks.

The one third-party SDK is the **Google Mobile Ads SDK** (with the User Messaging Platform for
consent), used only to show ads — see shared policy **§6.1**. There is no analytics SDK and no
crash-reporting SDK.

You can verify this inside the app: **Settings → About → Open Source Licenses.**

### G. Shared policy §9 — what you can delete in this app

**Settings → Data**: *Clear cache* · *Clear cookies (sign out)* · *Reset saved tabs* ·
*Clear Saved-Image Marks* (the green-outline record in §C; saved files are kept).
Each shows a confirmation once and cannot be undone. **Bookmarks are not affected** by any
of the four; delete those individually on the bookmarks screen.

**Settings → Diagnostics → Diagnostic log**: the *Clear* button empties the record.

**Saved images**: delete files and folders on the app's **Downloads** screen. If Easy NAS Photo
Viewer is installed, you can also delete them there in its iPhone Folder (§H).

**Ad consent**: Settings → Remove Ads → Ad Privacy Settings (shown only where consent is required).

**Everything at once**: deleting the app removes the above, with two exceptions: saved images stay
in the shared storage while Easy NAS Photo Viewer remains installed on the device (§H), and Keychain
items follow shared policy §3.1. The 8 synced settings in §C may remain on your other devices signed
in to the same Apple ID.

### H. Where saved images live — storage shared with the developer's other app

Saved images are stored on the device in a **shared storage area** (`Files/` inside the App
Group `group.com.jjsuite.shared`). It is **one folder** shared with the developer's app **Easy NAS Photo Viewer**.

- If that app is installed on the same device, it shows this folder as its iPhone Folder; files that
  app downloads from a NAS or receives through the share sheet land in the same folder and appear on
  the Downloads screen too. That app can open and delete the files, and upload them to your own server when you choose to. The files
  leave the device only when you upload them yourself from that app.
- This area is **not visible under "On My iPhone" in the Files app.** Use the app's Downloads screen
  and its Share button to take files elsewhere.
- Files that an earlier version saved in the app's own folder (`Documents/Downloads/`) are moved
  into this area the first time the updated app runs.
- Deleting this app leaves these files in place while Easy NAS Photo Viewer remains installed; they
  are removed when every app using the area has been deleted.

---

### I. Shared policy §7 — encryption and export compliance

This app uses only the HTTPS (TLS) provided by the operating system. It qualifies for the standard-encryption exemption under Category 5 Part 2 of the U.S. Export Administration Regulations and declares this in its app information (`ITSAppUsesNonExemptEncryption = false`).

---

*This document is available in English and Korean. In case of interpretive divergence, the
English version prevails.*
