# ListenWell — Releases

**Your library. Your files. Your player.**

ListenWell is a customizable music player for people who would rather own their music
than rent it. There is no catalog and nothing to discover — you upload your own audio
files, they are stored privately in your account, and you play them from any device
through an interface built for control rather than engagement.

### ⬇️ [Open the web app](https://listen-well-eight.vercel.app) · [Download the desktop app](https://github.com/soonavi/listenwell-releases/releases/latest)

---

## About this repository

This repository holds build artifacts only: installers for Windows, macOS and Linux,
plus the `latest*.yml` feeds the in-app updater polls.

**There is no source code here.** This repository exists so the update feed can stay
public while the application source is private — a private repository's release assets
are private too, and the updater fetches them anonymously with no token. Releases are
published automatically when a `v*` tag is pushed in the source repository. Nothing here
is meant to be edited by hand.

---

## Download & install

One account, three ways to listen. Your library, playlists, loved tracks, and play counts
live in your ListenWell account, so everything follows you between them.

### Web — nothing to install

Open **[listen-well-eight.vercel.app](https://listenwell.lol)** and sign in
or create an account with an email and password. This is always the newest build.

### Desktop — Windows, macOS, Linux

Every download lives on the
**[latest release](https://github.com/soonavi/listenwell-releases/releases/latest)** page,
under **Assets**. Pick the one file that matches your machine — the rest are for the
built-in updater and you can ignore them.

| Your machine | Download | Size |
| --- | --- | --- |
| Windows 10/11 (64-bit) | `ListenWell.Setup.<version>.exe` | ~108 MB |
| Mac with Apple Silicon (M1 or later) | `ListenWell-<version>-arm64.dmg` | ~128 MB |
| Linux (any distro, x86-64) | `ListenWell-<version>.AppImage` | ~141 MB |

The `latest*.yml` and `.blockmap` files are how the app finds and downloads its own
updates. You never need to download them by hand.

**Windows.** Run the installer. Windows will show a **"Windows protected your PC"**
screen — click **More info → Run anyway**. The app is unsigned, which is normal for
independent software and is not something the installer can suppress. You can choose the
install directory; then launch **ListenWell** from the Start menu.

**macOS.** Open the `.dmg` and drag ListenWell to Applications. The app is unsigned and
un-notarized, so the first launch is blocked: **right-click (or Control-click) the app →
Open → Open**. Double-clicking will only offer "Move to Bin". You only have to do this
once per installed version. If macOS insists the app "is damaged", clear the quarantine
flag and open it again:

```bash
xattr -dr com.apple.quarantine /Applications/ListenWell.app
```

> **Intel Macs are not covered.** The release builds Apple Silicon (`arm64`) only. On an
> Intel Mac, use the web app.

**Linux.** An AppImage needs no installation — mark it executable and run it:

```bash
chmod +x ListenWell-<version>.AppImage
./ListenWell-<version>.AppImage
```

Some distributions need FUSE 2 for AppImages (`sudo apt install libfuse2` on Debian and
Ubuntu). Failing that, `./ListenWell-<version>.AppImage --appimage-extract-and-run` works
without it.

**All three** need an internet connection, because your library lives in your account
rather than on the machine.

### Phone / tablet — install as an app

ListenWell is a PWA, so you can add it to your home screen and run it fullscreen without
an app store:

- **iOS (Safari):** open the site → Share → **Add to Home Screen**
- **Android (Chrome):** open the site → ⋮ menu → **Install app** / **Add to Home screen**

You get the app icon, a standalone window with no browser chrome, and the mobile layout:
a bottom player bar tinted from the current cover art, swipe-to-skip, and a
touch-draggable queue.

---

## Updating

Nothing you have to remember, on any platform except one.

### Web and phone — automatic

The web app deploys continuously, so loading the page gives you the newest build. The
service worker serves navigations network-first, which means an installed PWA picks up a
new version the next time you open it with a connection. There is no update button and
nothing to clear.

If a PWA ever looks stale, fully close it (swipe it away from the app switcher rather
than backgrounding it) and reopen it.

### Desktop — Windows and Linux, on a prompt

The desktop app checks for updates **once, at launch**, and never downloads anything
without asking:

1. If a newer version exists, a dialog offers **Download** or **Not now**.
2. Choose Download and it fetches in the background — only the changed chunks, not the
   whole installer, because of those `.blockmap` files.
3. When it finishes, a second dialog offers **Restart now** or **Later**. Choosing Later
   installs the update the next time you quit.

Declining costs nothing; it asks again the next time you start the app. A failed check
(no connection, GitHub unreachable) is ignored silently rather than interrupting you.

> **Updating from v0.2.4 or older.** Downloads used to live in a different repository,
> which is no longer public. Builds older than v0.2.5 look for updates there and will
> never find them — and a failed check is silent by design, so there is no error to see,
> just a prompt that never comes. Download v0.2.5 or newer from this page by hand once;
> it keeps itself current from then on.

### Desktop — macOS, by hand

**macOS is the exception: the in-app updater cannot update this app.** Applying an update
on macOS requires a valid code signature, and these builds are unsigned. The check runs
and fails quietly, so you will not see an error — you will simply never be prompted.

To update a Mac, download the new `.dmg` from the
[latest release](https://github.com/soonavi/listenwell-releases/releases/latest) and drag
it over the old app, right-clicking to open it the first time as above. Signing and
notarizing the macOS build would fix this and needs an Apple Developer account.

### What an update does not touch

Your library, playlists, loved tracks, play counts, and settings live in your ListenWell
account, not in the app. Updating, reinstalling, or moving to a different machine leaves
all of it intact — sign in and it is there.
