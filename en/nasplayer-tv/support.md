---
layout: default
lang: en
title: "Support — NAS Player"
permalink: /en/nasplayer-tv/support/
alt: /nasplayer-tv/support/
app: nasplayer-tv
kind: support
description: "Help for NAS Player on Apple TV: connecting a NAS, open source (LGPL) notice and how to contact the developer."
---

# Support

**Applies to**: NAS Player (tvOS · App Store name: Easy NAS Player TV) **Version**: 1.0

---

## About this app

NAS Player lets you **browse and play the photos and videos on your NAS or file server from Apple TV**.
It is the Apple TV edition of Easy NAS Photo Viewer for iPhone and iPad, **without upload or download** —
files are never copied to Apple TV or sent to the NAS; the app shows and plays them where they are.

- **Free · no ads · no in-app purchases**
- Servers you can connect to: **Synology NAS** (DSM), **SMB shared folders** (Windows, macOS, NAS) and **SFTP servers**
- Photos: full screen, previous/next with the remote, zoom, slideshow
- Videos: choice of playback engine, automatic resume, auto-play next file, subtitles (srt, smi, vtt) found automatically, subtitle style
- Folder browsing: thumbnail or list view, sort order, column count. File management on the server (new folder, rename, delete, move; compress and extract on Synology)

NAS Player is **a separate app** from the iPhone edition (Easy NAS Photo Viewer); they share no settings or credentials.

---

## Requirements

- **Apple TV** with tvOS 17.0 or later
- A Synology NAS (DSM 7.x recommended), SMB shared folder or SFTP server **that you own**
- Apple TV and the server on the same network, or the server reachable from outside

---

## Connecting your NAS

Add a profile under **Settings → NAS profiles**. You can register several profiles and switch between them.
Type with the tvOS keyboard, or with your iPhone keyboard when an iPhone signed into the same Apple Account is nearby.

### Synology NAS

1. **Server type**: `Synology`
2. **Address**: the LAN IP on the same network (e.g. `192.168.1.10`); from outside, a DDNS address or a **QuickConnect ID**
3. **Port and HTTPS**: DSM defaults are HTTP `5000` / HTTPS `5001`; use yours if you changed them
4. **Account and password**: your DSM account
5. **Two-factor authentication**: if 2FA is on for the account, turn on **Use two-step verification** and enter the OTP when you connect. Choose **Trust this device for 30 days** to skip the OTP during that time, or store the **OTP auto-generation seed (Base32)** so the app generates codes itself.
6. Confirm with **Test connection**.

If the NAS uses a self-signed certificate over HTTPS, a **certificate trust prompt** appears on first connection. Accept it and the app stores the certificate's fingerprint and checks it on later connections.

### SMB shared folder

1. **Server type**: `SMB`
2. **Address** (e.g. `192.168.1.20`), **share name**, and **domain** if needed
3. **Account and password** (leave the user name empty to connect as guest)

### SFTP server

1. **Server type**: `SFTP`
2. **Address, port** (default 22) and **start path**
3. **Authentication**: password or an OpenSSH private key (Ed25519 or RSA, passphrase supported)
4. On first connection the server's **host key fingerprint** is shown. Trust it to connect; if the server key later changes, the app refuses to connect.

### If you can't connect

1. Check the **address and port** again.
2. **Firewall** — make sure the port is not blocked in DSM Control Panel → Security → Firewall (or the server's firewall).
3. **Local Network permission** — tvOS asks once when the app first contacts a private IP (`192.168.x` and similar). If you declined, turn NAS Player on under Local Network in Apple TV's privacy settings so it can reach servers on your LAN.
   The app never discovers or scans for devices; it connects only to the address you entered.
4. **If a certificate keeps being rejected**, delete the profile and create it again to get a fresh trust prompt (a newly issued server certificate has a new fingerprint).

---

## FAQ

### Q. A video won't play

For videos on a Synology NAS, try another engine under **Settings → Videos → Default playback method**.

1. **Built-in VLC (VLCKit)** — the default. Almost every format, including MKV, AVI and WMV, with subtitles
2. **Direct playback (AVPlayer)** — Apple's player. MP4, MOV, H.264, HEVC
3. **Video Station (HLS)** — the NAS's Video Station transcodes and streams it. The package must be installed.
4. **High quality (mpv)** — GPU upscaling, debanding and sharpening to fit low-resolution video to your TV

Turn on **Show choice sheet on playback** to choose each time. Videos on SMB and SFTP servers play with built-in VLC.

**Playing Synology videos requires the NAS HTTP port (DSM default 5000) to be open.** The playback engines cannot share the
self-signed certificate trust stored by the app, so they connect over HTTP. If you only expose HTTPS, enable HTTP in the DSM Control Panel.

### Q. Subtitles don't appear

A `.srt`, `.smi` or `.vtt` file with the **same name** must be in the **same folder** as the video (for `movie.mkv`, use `movie.srt` or `movie.ko.srt`).
The encoding (UTF-8, CP949, EUC-KR and others) is detected automatically. Change size, colour, outline and background under **Settings → Videos → Default subtitle style**.

### Q. My video starts in the middle

That is **automatic resume**. To start over, choose **"From the beginning"** when playback starts.
To erase every record, use **Settings → Data → Clear resume history**.

### Q. Can I download files to Apple TV or upload them to the NAS?

**No.** The app has no upload or download feature. Photos and videos are read from the server and shown or played directly.
Thumbnails and images are kept in memory only for a while and disappear when the app is closed.

### Q. Do my settings sync to my other Apple TV?

**Not in version 1.0.** Settings are set per Apple TV (some preferences are written to the iCloud Key-Value Store but are not read back on other devices — see section 4 of the privacy policy).
**Your NAS address, account and password do not sync** — they are stored only in this device's Keychain (`ThisDeviceOnly`), so enter them again on a new device.

### Q. The app is always light / always dark

Choose System, Light or Dark under **Settings → Appearance**.

### Q. Something went wrong. What should I send?

**Settings → Diagnostics → Diagnostic log** shows recent activity. Apple TV has no share sheet, so the log cannot be exported —
a photo of the screen showing the error is fine. The log is never sent automatically.

### Q. Is this a Synology app?

**No.** This is an independent app, not made or endorsed by Synology Inc. `Synology`, `DSM`, `QuickConnect` and `Video Station`
are trademarks of Synology Inc., used here only to say which devices the app works with.

---

## Open source (LGPL)

NAS Player uses LGPL open-source libraries for video playback.

- **MPVKit** (mpv, FFmpeg, libplacebo and others; LGPL-2.1+ / LGPL-3.0+) — "High quality (mpv)" playback. Statically linked into the app executable.
- **TVVLCKit** (VLC, LGPL v2.1 or later) — "Built-in VLC" playback
- **AMSMB2** (with libsmb2, LGPL v2.1 or later) — SMB connections

For every build we publish, in the public repository below, the materials needed to relink the app with a modified LGPL library
(the app's object files, link command and instructions) together with each component's version and source location.

**Relinking materials and source requests**: [https://github.com/yjinchoi/nasplayer-relink](https://github.com/yjinchoi/nasplayer-relink)

**Written offer**: for **at least three years** after the last distribution of each build of NAS Player, we will provide anyone who asks
the **complete corresponding source code** of the LGPL libraries used in that build, together with the relinking materials,
for **no more than the cost of physically performing the distribution** (download links are free).
Please request it by opening a [GitHub issue](https://github.com/yjinchoi/nasplayer-relink/issues) in that repository (include the build number).

Full licence texts and per-component notices are also in the app under **Settings → About → Open source licenses**.

---

## Contact and bug reports

- **Email**: [yjinchoi0623@gmail.com](mailto:yjinchoi0623@gmail.com)

Including the following gets to a fix much faster:

- App version (Settings → About → Version)
- tvOS version and Apple TV model
- Server type (Synology DSM version, SMB or SFTP)
- Steps to reproduce — what you pressed and what happened

---

*This is an indie, one-developer project. Support is best-effort and response time may vary.*

*Synology, DSM, QuickConnect and Video Station are trademarks of Synology Inc. This app is not made or endorsed by Synology Inc. and is not affiliated with Synology Inc.*
