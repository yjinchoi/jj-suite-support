---
layout: default
lang: en
title: "Support — Easy Web Image Collector"
permalink: /en/webimage/support/
alt: /webimage/support/
app: webimage
kind: support
description: "Help for Easy Web Image Collector and how to contact the developer."
---

# Support

**Applies to**: Easy Web Image Collector (iOS) **Version**: 1.0

---

## Requirements

- **iOS 16.0 or later**
- iPhone and iPad

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

---

## FAQ — this app

### Q. I want to save many pictures in a row

**Touch and hold the bolt button.** Continuous save turns on, and every picture you tap is
saved until you tap the bolt again. The toolbar icon changes to a **bolt with an "A" badge**
(`bolt.badge.automatic.fill`) while it is on. A plain tap on the bolt saves one picture and
then turns itself off.

In continuous mode, **tapping a picture that is also a link saves the picture instead of
opening the link.** To follow the link, tap the bolt to turn the mode off first.

### Q. Some pictures have a green outline

**That marks pictures you have already saved.** It also appears on pictures the page loads
later as you scroll, and again when you come back to the page, so you can see how far you got.

- The same picture at a **different address** (a resized copy, a different query string) counts
  as a different picture and is not outlined.
- Pictures inside embedded frames (`iframe`) are not outlined.
- To clear the record, use **Settings → Data → Clear Saved-Image Marks.** Your saved files stay.
  The record (a list of saved picture addresses) lives only on your device and is never sent
  anywhere.

### Q. Where did my saved images go, and how do I move them elsewhere?

On the app's **Downloads** screen. They live in a shared storage area on the device, so they
**do not appear under "On My iPhone" in the Files app.** Use the **Share** button in the Downloads
folder and the viewer to send them to other apps, and **Save to Photos** in the viewer to put one in
the Photos app (the first time, iOS asks for permission to *add* photos — the library is never read).

If Easy NAS Photo Viewer is also installed, your saved images appear there under iPhone folders › Web
Images. Images an earlier version kept in the Files app under On My iPhone › WebImage › Downloads are
moved into this area the first time the updated app runs.

Change the folder in **Settings → Save → Default download folder** (subfolders work too). The
setting just below decides whether a name collision gets a number (`name (1).jpg`) or
overwrites.

### Q. Can this app upload to a NAS?

**No — there is no NAS feature in this app.** It contains no code that connects to a NAS or
to any other storage server, and it has no sign-in screen; the only things it connects to are
the websites you open yourself (apart from Google and the App Store, for ads and the ad-free
purchase). In exchange, there is nothing to configure: install it and it works.

Moving photos and videos between your iPhone and a Synology NAS is what the separate app
**Easy NAS Photo Viewer** does. The two apps are fully independent; neither requires the other.

### Q. Instant Save is on but tapping an image saves nothing

Check these:

- Is it actually on? When it is, the toolbar icon is a **filled bolt** with a short bar under
  it, and a message appears at the bottom of the screen each time you toggle it. A single tap
  on the bolt **turns off after one picture** — touch and hold it for continuous save.
- Did you tap the same image twice quickly? The same address is not saved twice **within one
  second** — this prevents a single tap from producing two files.
- Did you tap many images at once? At most **three** downloads run at a time; the rest **wait
  in line** and are saved in turn. Wait for the "waiting" message at the bottom to clear.
- Is it really an image? Artwork drawn as a CSS background or on a canvas cannot be saved.

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
