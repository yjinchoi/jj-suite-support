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
- Support page: [Easy NAS Download Manager Support]({{ '/en/torrent/support/' | relative_url }})

---

## App-specific details — Easy NAS Download Manager

### A. What this app stores in the Keychain (common policy §3.1)

Three items of its own. None of them leaves this device.

1. **NAS connection profiles** (`nas.profiles.v2`) — for each profile: a name; the server
   address or QuickConnect ID; port; whether HTTPS is used; the DSM username and
   **password**; whether two-factor authentication is enabled and, if you entered one,
   the **one-time-password seed**; the trusted-device identifier issued by DSM and its
   expiry; and your default and recently used destination folders.
2. **NAS certificate trust** (`certtrust.nas.v1`) — fingerprints of NAS certificates you
   approved.
3. **Website certificate trust** (`certtrust.browser.v1`) — fingerprints of website
   certificates you approved in the in-app browser. This is a **separate store** from (2);
   neither one leaks into the other.

Separately, the **ad-free status item** common to all three apps sits in the shared group
(common policy §3.1).

### B. Settings synced through iCloud (common policy §4)

**Six**, all of them settings rather than credentials: appearance; search engine;
JavaScript allowed; block pop-ups; the **identifier only** of the active NAS profile (no
address, account, or password); and the default destination folder path.

Bookmarks, cookies, diagnostic logs, your download task list, and items held in "waiting
to be added" are **not** synced.

### C. What this app connects to (common policy §6)

Only two kinds of destination that you choose, plus the ads (Google) and the ad-free purchase
(Apple App Store) common to all three apps (common policy §6.1, §6.2).

1. **The Synology NAS you configured** — to list tasks and to create, pause, resume, and
   delete them, and to sign in. If you use a QuickConnect ID, resolving it contacts
   **Synology's QuickConnect service**; that happens only when you turn that option on.
2. **Websites you open yourself in the in-app browser.** You type the address. The app
   preloads no site, and offers no site list or recommendation. Address-bar searches go
   to the general search engine you pick in Settings (Google, DuckDuckGo, or Bing).

The app downloads no content files — no video, no music. The only thing it fetches
itself is the `.torrent` metadata file (typically tens of kilobytes) it hands to the NAS,
and only when a login-protected site prevents the NAS from fetching it. That file is
uploaded straight to your NAS; it is not retained and no third party is involved. The
download is performed by Download Station on your own NAS.

There is no developer-operated server.

### D. Permissions the app requests

**Two.**

- **Local network access** — iOS asks once when your NAS is on the same network at a
  private IP address. The app **does not discover or scan for devices**; it connects only
  to the address you typed in NAS settings.
- **App Tracking Transparency** — common to all three apps. Asked once after ad consent; allow it
  for personalized ads, otherwise ads are non-personalized (common policy §6.1). Change it in iOS
  Settings › Privacy & Security › Tracking.

Not requested: photos, camera, microphone, location, contacts, notifications, health,
calendar. The corresponding usage strings are absent from the app's Info.plist and the
corresponding APIs are never called.

### E. Third-party libraries

**No open source.** This app links no third-party open-source library; the app's "Settings →
Open source licenses" screen states the same.

The one third-party SDK is the **Google Mobile Ads SDK** (with the User Messaging Platform),
common to all three apps and used only to show ads — see common policy §6.1. There is no
analytics or third-party crash-reporting SDK.

### F. What you can delete inside the app (common policy §9)

| What | Where | What goes |
|---|---|---|
| Web data | Settings → Browser → **Clear web data** | Browser cookies, cache, and site logins. NAS profiles and bookmarks stay |
| Browser certificate trust | Settings → Browser → **Reset browser certificate trust** | Website certificate fingerprints only; NAS trust stays |
| A NAS profile | Settings → NAS → NAS profiles → the profile → **Delete this profile** | That profile's address, account, password, OTP seed, and trusted-device token |
| Device trust | NAS connection settings → Security → **Revoke trust for this device** | The trusted-device token issued by DSM |
| Diagnostic log (on screen) | Settings → About → Diagnostics → **Clear on-screen log** | The in-memory record; session files remain |
| Ad consent | Settings → Remove Ads → **Ad Privacy Settings** (shown only where consent is required) | Your Google ad-consent choice (common policy §6.1) |

Deleting the app removes all of the above and any `.torrent` files held in "waiting to be
added". Keychain items follow common policy §3.1. Individual held items can be deleted by
you, and old ones expire on their own.

### G. When plain HTTP is used, and why (common policy §7)

There are **only two cases**.

1. **Your NAS does not offer HTTPS.** A home NAS usually sits on the LAN, and DSM's default
   is plain HTTP on port 5000. If you have not enabled HTTPS for the NAS, the connection is
   in the clear; if you have, the app uses HTTPS — it never downgrades one that works.
2. **A site you open in the in-app browser uses HTTP.** It is a general-purpose browser, you
   may open any site, and some sites still do not use HTTPS.

In both cases the other end is **your own NAS, at an address you typed**, or **a website you
opened yourself**. No connection goes to the developer in either case. A certificate that
fails validation stays blocked until you explicitly approve that host, and NAS trust and
browser trust are kept in the separate stores described in §A.

---

*This document is available in English and Korean. In case of interpretive divergence, the
English version prevails.*
