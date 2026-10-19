---
layout: default
lang: en
title: "Support — Easy NAS Download Manager"
permalink: /en/torrent/support/
alt: /torrent/support/
app: torrent
kind: support
description: "Help for Easy NAS Download Manager and how to contact the developer."
---

# Support

**Applies to**: Easy NAS Download Manager (iOS) **Version**: 1.0

---

## About these apps

The developer publishes **three independent iOS apps**. Install only the ones you need — none
of them requires the others.

| App | What it does | Synology NAS required |
|---|---|---|
| **Easy Web Image Collector** (Home Screen: `WebImage`) | Tap images in a web browser to download them to your iPhone | **No** — works right after install, no setup |
| **Easy NAS Photo Viewer** (Home Screen: `NASPhoto`) | View photos and videos on your iPhone and on your Synology NAS (or an SMB shared folder), and move files between them | Yes (an SMB shared folder also works) |
| **Easy NAS Download Manager** (Home Screen: `Downloads`) | Remotely manage Download Station on the Synology NAS you own | **Yes (required)** |

The three apps **do not share credentials or settings.** Each is configured separately (see FAQ).
The only thing they share on the same device is the ad-free purchase status.

---

## Requirements

- **iOS 16.0 or later**
- iPhone and iPad
- **A Synology NAS you own** (DSM 7.x recommended) — NAS Photo Viewer also works with an SMB shared folder

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

## FAQ — Download Station

### Q. The NAS connects, but the task list is empty and shows an error

The **Download Station package must be installed** on your NAS. Install it from DSM's
Package Center and try again. This app only drives Download Station; it provides no
downloading of its own.

### Q. Which DSM account should I use?

**Any account allowed to use Download Station is enough.** The app never asks for file
browsing (File Station) rights, so it does not need an administrator account. The
"Test connection" button in NAS settings signs in and reads the task list once to confirm.

### Q. The destination picker doesn't list my NAS folders

That is intentional — the app **does not browse folders on your NAS**. Pick a destination
in one of three ways:

1. **DSM default** — choose nothing and the file lands in Download Station's own default
   download folder. This is usually all you need.
2. **A folder you used recently.**
3. **A path you type** — a relative path starting at the shared folder name, e.g.
   `download/tasks`. **Do not start it with `/` or `/volume1/`** (the app strips those,
   but typing a relative path from the start is safer).

### Q. Do downloads stop when I quit the app?

**No.** Your NAS does the downloading. The app is a window onto it, so closing the app —
or turning the phone off — changes nothing. Reopen it and you see where things got to.

### Q. Where on my iPhone are the files saved?

Nowhere. Files land in the destination folder **on your NAS**. This app has no feature for
downloading files to the iPhone.

### Q. What is "waiting to be added"?

A holding area for items found before your NAS was connected, or ones whose registration
failed. Connect the NAS and register them together from there. Old items expire on their
own, and you can delete any of them.

### Q. What is the extraction password for?

It is the password Download Station uses when it automatically unpacks the result.
**Leave it empty** unless you know you need it — it is used by your NAS, not by the app.

### Q. I think I added the same thing twice

The add screen flags items that look like they are already downloading, but it **does not
block the selection** — DSM's idea of a duplicate and the app's information do not always
match, so it will not claim certainty. If it turns out to be a duplicate, delete one from
the task list.

## FAQ — Collecting links in the browser

### Q. The page clearly has links, but it says "No download tasks on this page"

The app finds links that **actually exist in the page**. It will miss them when:

- the link is produced only by running JavaScript,
- the address is generated after you press a button, or
- the page has not finished loading (the count on the centre button updates when it does).

In those cases, just **tap the link itself** — files fetched that way arrive at the same
confirmation screen.

### Q. What does the "needs checking" badge mean?

The address alone is not enough to tell whether it is a `.torrent` file. When you select it
and the app actually fetches it, the file format is checked, and anything in the wrong
format is dropped right there. **Only what passes the check reaches your NAS.**

### Q. I tapped a link and got a login page instead of a file

That is the format check catching it. Sign in to the site first and try again — sessions
persist inside the app's browser.

### Q. Can it add files from sites that require a login?

Yes. When your NAS cannot fetch the file itself, the app fetches the `.torrent` file
(usually tens of kilobytes) and uploads it to your NAS. The downloading that follows is
still done by the NAS.

### Q. The browser has no start page or site list

By design: the app **recommends no site and ships no site list**. You type the address,
and keep the ones you return to in bookmarks. Address-bar searches go to the general
search engine you pick in Settings (Google, DuckDuckGo, or Bing).

## FAQ — Handoff from other apps

### Q. I tapped a magnet link elsewhere and a different app opened

When several apps can open magnet links, iOS picks one, and **an app cannot decide which**. The
reliable route is to copy the link and paste it on this app's "Add Download Task" screen — a
button appears there when the clipboard holds a magnet link.

### Q. Can I open a `.torrent` file from the Files app?

Yes. Use "Open in" from the Files app or any share sheet and pick this app; the
confirmation screen opens.

### Q. Can this app download files to my iPhone?

No. This app is a **remote control for Download Station on your NAS**. Moving photos and
videos between an iPhone and a NAS is a different app's job (Easy NAS Photo Viewer).

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

## FAQ — the in-app web browser

### Q. Do site logins persist?

Yes. Cookies are kept in WebKit's standard store. Clearing cookies from Settings logs you out of
every site. (Depending on the app that is a separate "Delete cookies" action, or a single
"Clear web data" that removes cache and cookies together.)

### Q. A site doesn't render properly

- Check whether **Allow JavaScript** is off in the browser settings. Changes apply from the next
  page load.
- With **popup blocking** on, links that open a new window will not work.
- If it still fails, clear the cache (or web data) and reload.

### Q. A site is asking for a username and password. Is it saved?

No. Credentials entered for HTTP authentication are kept **for that run of the app only** and are
never written to the Keychain. You will be asked again after a restart.

### Q. The browser shows a certificate warning

Trust is stored only for hosts you approve. That store is **entirely separate from NAS connection
trust**, so trusting a website has no effect on how NAS connections are validated. Do not approve
sites you do not recognize.

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
