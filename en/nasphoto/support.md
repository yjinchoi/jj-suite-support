---
layout: default
lang: en
title: "Support — Easy NAS Photo Viewer"
permalink: /en/nasphoto/support/
alt: /nasphoto/support/
app: nasphoto
kind: support
description: "Help for Easy NAS Photo Viewer and how to contact the developer."
---

# Support

**Applies to**: Easy NAS Photo Viewer (iOS) **Version**: 1.0

---

## About these apps

The developer publishes **three independent iOS apps**. Install only the ones you need — none
of them requires the others.

| App | What it does | Synology NAS required |
|---|---|---|
| **Easy Web Image Collector** (Home Screen: `WebImage`) | Tap images in a web browser to download them to your iPhone | **No** — works right after install, no setup |
| **Easy NAS Photo Viewer** (Home Screen: `NASPhoto`) | View photos and videos on your iPhone and on your Synology NAS (or an SMB shared folder or SFTP server), and move files between them | Yes (an SMB shared folder or SFTP server also works) |
| **Easy NAS Download Manager** (Home Screen: `Downloads`) | Remotely manage Download Station on the Synology NAS you own | **Yes (required)** |

The three apps **do not share credentials or settings.** Each is configured separately (see FAQ).
The only thing they share on the same device is the ad-free purchase status.

---

## Requirements

- **iOS 16.0 or later** (Easy NAS Photo Viewer: **iOS 17.0 or later**)
- iPhone and iPad
- **A Synology NAS you own** (DSM 7.x recommended) — NAS Photo Viewer also works with an SMB shared folder or an SFTP server

---

## FAQ — common to all apps

### Q. Do these apps collect my data?

The developer does not. There is no developer-operated server and the app sends the developer
no requests. No analytics SDK and no third-party crash reporting.

The apps are free and show **Google AdMob ads**; to load them, the Google SDK inside the app sends
some device data to Google. On first launch iOS shows a **tracking permission** prompt once — allow it
and you may see ads matched to your interests (using the advertising identifier); don't, and you see
non-personalized ads only. Either way the app works the same and shows the same number of ads. See the
Privacy Policy for details.

### Q. How do I turn personalized ads (tracking) on or off?

Use this app's switch in **iOS Settings › Privacy & Security › Tracking**. Turn it off and later ad
requests are non-personalized. In the European Economic Area, the UK and similar regions you can also
change your Google ad consent in the app under **Settings → Remove Ads → Ad Privacy Settings**.

### Q. Do my settings sync between iPhone and iPad?

**Some settings do.** Appearance, search engine, sort order, default folder choices and similar
values travel to your other devices signed into the same Apple ID via Apple's iCloud Key-Value
Store. There is no in-app toggle; it runs quietly.

**Credentials do not sync.** Your NAS address, account, password, and two-factor seed are stored
in the iOS Keychain as **this-device-only** (`ThisDeviceOnly`), so they never travel to another
device and are not included in device backups. On a new device you **enter them again**.

> The predecessor app (SynoBrowser) documented credentials as syncing via iCloud Keychain.
> Verification against the code showed that was not the case; this document corrects it.

To stop settings sync entirely: iOS Settings → [your name] → iCloud → turn iCloud off for the app.

### Q. Does anything remain after I delete the app?

Deleting the app removes its local data — files in its own folder and its settings. A few things
can remain:

- Settings already synchronized to iCloud may still exist on your other devices signed into the
  same Apple ID.
- iOS does not guarantee that deleting an app deletes its Keychain items. To be sure a stored
  account is gone, delete the profile inside the app first. The ad-free purchase record stays for
  the other two apps.
- Web Image Collector and NAS Photo Viewer keep files in a storage area the two apps share. While
  one of them is still installed, those files remain.

### Q. How do I clear stored data from inside the app?

The Settings screen has controls for clearing stored data. **Where they live and what they are
called differs per app** — some collect them under a "Data" section, others offer a single
"Clear web data" under "Browser". Each asks for confirmation once, and the action
**cannot be undone**.

### Q. The app is always light / always dark

**Settings → Appearance** — choose Light, Dark, or System. The default is System.

### Q. Something went wrong. What should I send?

The **Diagnostic Log** in Settings shows the running record and can export it via the share
sheet. (Depending on the app it sits under "Diagnostics" or "About".)

The log stays on your device and is **never transmitted automatically** — it leaves only when you
send it. It may contain timestamps and outcomes of operations, error messages, and the address
and request path of servers the app contacted. It does not contain passwords or two-factor seeds,
and server session keys are masked before being written. **Please send it knowing that.** You are
welcome to write in without attaching one.

### Q. All three apps use the same NAS — why configure each one separately?

That is deliberate. The three apps **do not share the Keychain store that holds credentials**; each
has its own access group so that no app can read another's credentials (the only record all three
read is the ad-free purchase status). The cost is entering the NAS address,
account, two-factor settings, and certificate trust once per app.

---

## FAQ — this app

### Q. Where do I choose between upload and download?

**You don't.** Where a file is decides where it goes.

- Select files in a NAS folder → they **download** to your iPhone.
- Select files or folders in an iPhone folder → they **upload** to the NAS.

That is why there is no direction switch in the app. Only uploads ask where files should land;
downloads always go to the iPhone's "Downloads" folder.

### Q. I can't download a whole folder from the NAS

Correct — **NAS to iPhone works on files only**. If a folder is part of your selection the
download button turns off, because the API this app uses does not offer a way to have DSM bundle
a folder for download.

The other direction does work: **iPhone to NAS accepts folders**, and the subfolder structure is
recreated on the NAS.

### Q. I want to upload photos from the iOS Photos app

On an iPhone folder screen, tap **Upload from Photo Library…** (or the upload button → **Choose from
Photo Library**) to open iOS's photo picker. Pick photos and videos, choose the NAS folder, and they are
uploaded in their original format.

The picker is a system screen separate from the app, so the app receives **only the items you pick** —
which is why it never asks for permission to read your photo library.

Alternatively, in Photos tap Share and choose this app; the items land in "Received", and you can
upload them from there.

### Q. Can I switch apps during a transfer?

**Uploads (iPhone to NAS) keep going.** They are handed to iOS background transfer, so they continue
when you lock the screen or switch apps; results that finish while the app is away show up the next
time you open it.

**Downloads (NAS to iPhone) do not support background transfer.** Keep the app on screen while receiving.

If a whole-folder upload fails partway, **the files already uploaded stay on the NAS** — deleting
them was judged the more dangerous option. Check the failure count on the progress screen and
upload again; your Settings → Upload → "Rename automatically on conflict" choice applies.

### Q. A video won't play

Try a different engine. Settings → Video → **Default playback method** offers four:

1. **Built-in VLC** — the widest codec and container coverage. MKV, AVI, WMV and FLV usually open here.
2. **Direct playback (AVPlayer)** — Apple's own. Smoothest for MP4, MOV, H.264 and HEVC, with PiP and AirPlay.
3. **Video Station** — the NAS transcodes and streams it. The Video Station package must be installed on the NAS.
4. **Open in another app** — hand the file to VLC for iOS or another player.

To choose per video, turn on Settings → Video → **Show the picker on playback**.

**Playing NAS videos requires the NAS HTTP port (DSM default 5000) to be open.** The playback
engines each use their own network stack and cannot share the self-signed certificate trust the app
has stored. If you only expose HTTPS, enable HTTP in the DSM Control Panel. (Synology's own DS file
client works the same way.)

### Q. Subtitles don't appear

A `.srt`, `.smi` or `.vtt` file with the **same name** must sit in the **same folder** as the video.
For `movie.mkv`, use `movie.srt` or `movie.ko.srt`.

- If a `.smi` (SAMI) file contains several language classes, each becomes a **separate track** you
  can switch between during playback.
- Encoding is detected automatically — UTF-8, CP949, EUC-KR, Shift-JIS and Big5.
- Size, colour, outline and background are in Settings → Video → **Default subtitle style**, and
  changes apply while a video is playing.

### Q. My video starts in the middle

**That is automatic resume.** Reopen a video you were watching and it continues from where you
stopped. Nothing to choose, nothing to enable.

To start over, tap **"From the beginning"** on the chip that appears briefly when playback starts,
or drag the scrubber to zero. A video you watched to the end clears its own record.
To erase every record, use Settings → Data → **Clear resume history**.

### Q. What is the difference between "Received" and "Downloads"?

- **Received** — files that came in **from outside**, through another app's share sheet or the Files app.
- **Downloads** — files this app **fetched from the NAS**.

Both live in the "iPhone folders", a shared storage area on the device used together with Easy Web
Image Collector (images that app saves appear in the "Web Images" folder), so they are **not visible
under "On My iPhone" in the Files app.** Files you put into this app's folder through Files or Finder
on a Mac are moved into the iPhone folders on the next launch.

### Q. What licence does the built-in VLC playback use?

VideoLAN's **MobileVLCKit (LGPL v2.1 or later)** is embedded as a dynamic framework. The licence,
the copyright and a link to the source repository are in **Settings → Open Source Licences** inside
the app. No GPL-only plugins are bundled. The other open-source components are **AMSMB2 (with
libsmb2, LGPL v2.1 or later)** for SMB connections and **Citadel** (MIT) with its dependencies
(swift-nio-ssh, swift-nio, swift-crypto/BoringSSL, swift-asn1, swift-log, swift-atomics,
swift-collections, swift-system, BigInt) for SFTP; the only non-open-source third-party code is the
Google Mobile Ads SDK, used to show ads. All are listed under **Settings → Open Source Licences**.

### Q. Is this a Synology app?

**No.** This is an independent app, not made or endorsed by Synology Inc. `Synology`,
`DiskStation`, `DSM`, `QuickConnect` and `Video Station` are trademarks of Synology Inc., used
here and in the App Store description **only to say which device the app works with**. Please
send support questions to the address below, not to Synology.

---

## FAQ — connecting to a NAS

### Q. I can't reach my NAS

Check these in order.

1. **Address** — on the same Wi-Fi use the LAN IP (e.g. `192.168.1.10`); from outside use DDNS
   or a QuickConnect ID.
2. **Port** — DSM defaults are HTTP `5000` / HTTPS `5001`. Use your own if you changed them.
3. **HTTPS with a self-signed certificate** — DSM's self-signed certificate triggers a trust
   prompt on first connection. Declining it blocks the connection.
4. **Firewall** — verify the port isn't blocked under DSM Control Panel → Security → Firewall.
5. **Two-factor authentication** — enter the OTP, or store the OTP seed in Settings so the app
   can generate codes itself.

### Q. Why does it ask for "Local Network" access?

Since iOS 14 the system asks once when an app first contacts a private IP (`192.168.x`, `10.x`,
and similar) — which is what a NAS at home usually is. **The app does not discover or scan for
devices**; it connects only to the address you typed into Settings. Denying this permission
prevents the app from reaching a NAS on your LAN.

### Q. My self-signed certificate keeps being rejected

Run a connection to that NAS profile once from Settings and accept the trust prompt. The app
stores the **fingerprint** of the certificate you approved and checks it on later connections.
If the server issues a new certificate the fingerprint changes and you are asked again — the
most reliable fix is to delete the profile and create it anew.

### Q. Can I use more than one NAS?

Yes. Register several NAS profiles in Settings and switch between them. Address, account,
two-factor settings and folder choices are kept independently per profile.

### Q. My profiles don't appear on my other device

Credentials never leave the device (see the common FAQ above). Create the profile again on the
new device.

---

## Bug reports and feature requests

- **Email**: [yjinchoi0623@gmail.com](mailto:yjinchoi0623@gmail.com)

Including the following gets to a fix much faster:

- App name and version (Settings → About → Version)
- iOS version and device model
- DSM version (for NAS-related problems)
- Steps to reproduce — what you tapped and what happened
- Optionally, a diagnostic log — please read the common FAQ above about what it contains first

---

*These are indie, one-developer apps. Support is best-effort and response time may vary.*

*Synology, DiskStation and Download Station are trademarks of Synology Inc. These apps are not
made or endorsed by Synology Inc. and are not affiliated with Synology Inc.*
