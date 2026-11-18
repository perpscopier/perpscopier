# Updates

PerpsCopier updates itself. You don't need to download new versions by hand.

## How it works

1. The app checks for updates about 30 seconds after it starts, then every 6 hours.
2. A new version **downloads in the background**. Copying is not interrupted.
3. When it is downloaded, a banner says **Version … is ready to install**, and a notification tells you.
4. The update installs in one of three ways:

| Way | When |
|---|---|
| **Restart now** (banner) or **Restart to update** (Settings) | Right away, when you press it |
| **Automatically** | When **all your connected accounts are flat** (no open positions and no working futures orders) for 10 minutes **and** the computer has been **idle** (no keyboard or mouse) for 10 minutes |
| When you quit | The next time you quit the app from the tray |

The app never restarts by itself while a connected account has an open position or working futures orders, or while you are using the computer.

## During the restart

Restarting stops copying for a few seconds. If **Keep copying after a restart** is on in Settings (the default), copying turns back on by itself after the update.

## Check now

**Settings → Updates → Check now** checks right away. The Updates card shows:

- "You have the latest version."
- "Downloading version … %"
- "Version … is ready."
- "Could not check for updates: …" (try again later)

## Release notes

Every version is listed under [releases](https://github.com/perpscopier/perpscopier/releases) in this repository.
