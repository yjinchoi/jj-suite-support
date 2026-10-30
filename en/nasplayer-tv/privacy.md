---
layout: default
lang: en
title: "Privacy Policy — NAS Player"
permalink: /en/nasplayer-tv/privacy/
alt: /nasplayer-tv/privacy/
app: nasplayer-tv
kind: privacy
description: "What information NAS Player for Apple TV handles, where it is stored and who it talks to."
---

# Privacy Policy

**Applies to**: NAS Player (tvOS · App Store name: Easy NAS Player TV)
**Last updated**: 2026-10-30 **Version**: 1.1

---

## 1. Summary

The developer does not collect any user data.

There is no developer-operated server, and the app has no network connection to the developer. Your data moves only between your Apple TV and the servers (NAS or file servers) you set up yourself. The developer has no access to it.

NAS Player is **free, with no ads and no in-app purchases.** It contains no advertising, analytics or crash-reporting SDK and does not track you.
It also has **no upload or download feature.** It reads photos and videos from your server to show and play them; it never downloads files to keep on Apple TV and never uploads data from Apple TV to a server.

## 2. Principles

- **No tracking.** The app does not request App Tracking Transparency (ATT) permission and never reads the advertising identifier (IDFA) or any other device identifier.
- **No advertising, analytics or crash-reporting SDKs.** The only third-party libraries are open-source components for video playback and server connections (§8), with no data-collection, analytics or advertising functions.
- **No data is sent to the developer.** Usage history, device information and error reports are never transmitted to the developer.
- **No sale or sharing of user data.** The developer does not hold any user data in the first place.

## 3. What the app stores on your device

### 3.1 Keychain — server profiles and trust records

Sensitive information such as NAS addresses and accounts is stored in the tvOS Keychain for this app only (service `com.nasplayer.tv.keychain`, access group `$(AppIdentifierPrefix)com.nasplayer.tv`) and is not shared with any other app.

1. **Server profiles** (`nas.profiles.v2`)
   - All servers: server type, profile name, address, port, account name, password, folder settings (start folder and recent folders), profile identifier (UUID).
   - Synology NAS: whether QuickConnect ID and HTTPS are used, the two-factor (TOTP) seed if you enter one, and the device-trust token issued by DSM with its expiry.
   - SMB servers: share name and domain.
   - SFTP servers: start path, authentication method (password or private key), the OpenSSH private key and passphrase you enter, and the server host-key fingerprint you trusted on first connection.
2. **NAS certificate trust fingerprints** (`certtrust.nas.v1`): fingerprints of self-signed certificates you approved, used only for comparison on later connections.

Items are stored with `kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly`. They are not synced through iCloud Keychain and are excluded from device backups, so they **never leave this Apple TV.**

### 3.2 App preferences (UserDefaults)

Values such as appearance, sort order, view mode, grid columns, playback engine, subtitle style, video resume points and the last browsed location are kept in standard local storage (UserDefaults), accessible only to this app.

### 3.3 Images and temporary files

- Thumbnails and photos are kept **in memory only** while shown and disappear when the app is closed.
- When a video is played with Built-in VLC or High quality (mpv) and has a subtitle file of the same name, the app detects its encoding and keeps a UTF-8 copy in the device's temporary folder to attach it to playback. This is a transient part of playback, not a user-facing download feature.

### 3.4 Photos library (1.1)

- When you open "Photos Library" or "Albums", tvOS asks once for photo access. If you allow it, the app only **reads** this Apple TV's photo library, albums and shared albums — it never deletes, edits or creates photos.
- Photos and videos stored only in iCloud are fetched to the device from Apple's iCloud Photos service so they can be shown. tvOS handles this; nothing goes to the developer.
- Photos are kept in memory only while shown; originals are not stored separately and are never sent to a NAS or any other server. Some videos may be exported briefly to a temporary folder for playback.
- Original photos and videos are never stored on Apple TV.

## 4. What is written to iCloud — settings only

When you change settings, the app writes some preferences to Apple's iCloud Key-Value Store (identifier `$(TeamIdentifierPrefix)com.nasplayer.tv`, used by this app only). **Version 1.0 does not read these values back on your other Apple TVs** — settings stay per device.

- Written: appearance, grid columns, NAS list sort field and direction, folder view mode, active profile identifier (UUID), skip interval, default playback engine, whether to show the playback picker, auto-play next video, upscaling/sharpening, slideshow interval. Because the app shares its settings format with the iPhone edition, two upload-related values (default upload folder path, auto-numbering on name conflict) are also written, although NAS Player has no upload feature.
- Not written: all credentials including passwords, original photos and videos, video resume points, last location, recent folders, diagnostic logs.
- The data is kept in your iCloud account and the developer cannot access it. There is no in-app switch for this; nothing is written when you are signed out of iCloud.

## 5. Diagnostic log

The app keeps a diagnostic log on the device to help find the cause of problems.

- It consists of recent entries shown on screen (in memory, up to 500) and session log files inside the app's container (only the latest 10 are kept).
- **It is never transmitted.** The tvOS edition has no way to export it.
- Contents: times and outcomes of operations, error messages, and the address and request path of servers contacted. Passwords and two-factor seeds are never written, and server session keys are masked.

## 6. Who the app talks to

The app communicates only with **servers you enter in its server settings**: Synology NAS, SMB file servers (Windows, macOS or NAS shared folders) and SFTP servers.

- You choose the address (LAN IP, public domain or IP, or a Synology QuickConnect ID), the port and whether to use HTTPS.
- Only when you use a QuickConnect ID, the app queries Synology's QuickConnect lookup server (`global.quickconnect.to`) to turn that ID into a reachable address.
- The app never discovers or scans for devices (no Bonjour/mDNS browsing, no subnet scanning).
- There is no in-app web browser, so the app does not visit arbitrary websites.
- **No upload or download.** The only exchanges with your server are folder listings, reading photos, videos and subtitles for display and playback, and server-side file management you start yourself (new folder, rename, delete, move, compress, extract).
- On first connection to an SFTP server the app shows the host-key fingerprint and connects only if you trust it; if the key later changes, the connection is refused.
- There is no developer-operated server, and the app sends no network requests to the developer. Apple system services (iCloud Key-Value Store, iCloud Photos, App Store) are handled by tvOS.

## 7. Security

- **Encrypted connections first**: when the server supports HTTPS and you enable it, the app connects over HTTPS (TLS). SFTP uses SSH, which encrypts both authentication and file data.
- **When plaintext is used**: the app sets `NSAllowsArbitraryLoads = true`, and unencrypted transport is used in three cases, always to a personal server whose address you entered:
  1. When the NAS does not use HTTPS — Synology DSM defaults to HTTP (port 5000).
  2. Synology video playback — the playback engines cannot share the self-signed certificate trust stored by the app, so they connect to the NAS's HTTP port.
  3. SMB servers — the app uses SMB 3 signing and authentication but not SMB 3 transport encryption; it assumes a trusted home or office network.
- **Certificate validation**: certificate fingerprints are stored and checked only for hosts you approved. Certificate errors on hosts you have not approved block the connection.
- **Encryption and export compliance**: the app uses only standard encryption (TLS, and SSH for SFTP) and answers App Store Connect's export-compliance questions accordingly. The app is not distributed in France.

## 8. Permissions and third-party libraries

| Permission | Purpose |
|---|---|
| Local Network (`NSLocalNetworkUsageDescription`) | To reach NAS, SMB and SFTP servers on private IP addresses (e.g. 192.168.x.x). tvOS asks once on first connection. |
| Photos (`NSPhotoLibraryUsageDescription`, 1.1) | To view this Apple TV's photo library and albums on the TV and play slideshows (read-only). Asked the first time you open "Photos Library" or "Albums"; NAS features keep working if you decline. |

No other permission is requested — no location, contacts, microphone, camera or tracking (ATT).

All bundled third-party libraries are open source:

- **TVVLCKit 3.7.3** (VideoLAN, LGPL v2.1 or later) — "Built-in VLC" playback and playback of SMB and SFTP videos
- **MPVKit 1.1.0-n9.0.2** (mpv, FFmpeg, libplacebo and others; LGPL-2.1+ / LGPL-3.0+) — "High quality (mpv)" playback
- **AMSMB2** (with libsmb2, LGPL v2.1 or later) — SMB connections
- **SFTP**: Citadel (MIT) and its dependencies such as swift-nio-ssh, swift-nio and swift-crypto (including BoringSSL)

These libraries contain no data-collection, analytics or advertising functions. LGPL relinking materials and the written offer for source code are in the [Open source section of the support page]({{ '/en/nasplayer-tv/support/' | relative_url }}) and at [https://github.com/yjinchoi/nasplayer-relink](https://github.com/yjinchoi/nasplayer-relink). Full licence texts are in the app under Settings → About → Open source licenses.

## 9. Children's privacy

The developer does not collect personal information from anyone, including children under 13. All data stays on your Apple TV and your own servers.

## 10. Your choices and how to delete data

- **Server profiles and credentials**: delete a profile under Settings → NAS profiles; its address, account details, 2FA token and recent folders are removed from the Keychain. Files on the server are not affected.
- **Resume history**: Settings → Data → Clear resume history.
- **Image cache**: Settings → Data → Clear image cache (memory only; also cleared when the app closes).
- **Diagnostic log**: clear the on-screen entries under Settings → Diagnostics → Diagnostic log.
- **Deleting the app** removes the settings and files in its container. tvOS does not guarantee that Keychain items are removed with the app, so delete your profiles in the app first to be sure. Settings already written to iCloud may remain in your iCloud account.

Because the developer holds no user data, there is nothing to request from the developer for access, correction or deletion.

## 11. Changes to this policy

Material changes will be announced in the App Store release notes ("What's New") and reflected in the date at the top of this page.

## 12. Contact

- Email: [yjinchoi0623@gmail.com](mailto:yjinchoi0623@gmail.com)
- Support page: [NAS Player Support]({{ '/en/nasplayer-tv/support/' | relative_url }})

---

*This policy is provided in Korean and English. If the two differ in interpretation, the English version prevails.*
