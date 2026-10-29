# Cellar setup guide

From nothing to playing a Windows Steam game in about 15 minutes. Back to the [README](../README.md).

**The short version:** install Rosetta → install Cellar → **Runtimes** → download **Wine Staging** → **⌘N**: make a bottle on Wine Staging → **Install Steam** → sign in → install a game → **Play**.

## Contents
1. [Before you start](#before-you-start)
2. [Install Rosetta](#1-install-rosetta)
3. [Install Cellar](#2-install-cellar)
4. [Get a runtime](#3-get-a-runtime)
5. [Create a bottle](#4-create-a-bottle)
6. [Install your games](#5-install-your-games)
7. [Play](#6-play)
8. [Bottle settings](#bottle-settings)
9. [Updating Cellar](#updating-cellar)
10. [If a game won't start](#if-a-game-wont-start)
11. [Where things are](#where-things-are)
12. [Removing things](#removing-things)

---

## Before you start

| You need | Notes |
|---|---|
| macOS 26 or later | Cellar uses macOS 26's Liquid Glass design |
| A Mac with Apple silicon | Recommended. Intel Macs can use the Wine Staging runtime only |
| Rosetta 2 | Wine and Windows games are Intel code |
| About 3 GB free, plus room for games | Wine Staging is 703 MB unpacked, a bottle about 335 MB, Steam about 1.8 GB. The Game Porting Toolkit, if you add it, is another 780 MB |

**Won't work:** games with kernel-level anti-cheat, such as Valorant, Fortnite, and many online shooters and battle royales. No translation layer can run them.

## 1. Install Rosetta

Skip this if you've run an Intel app on this Mac before. Otherwise, in Terminal:

```bash
softwareupdate --install-rosetta --agree-to-license
```

## 2. Install Cellar

1. Download **Cellar-x.y.z.zip** from the [latest release](https://github.com/alimicious/cellar-releases/releases/latest) and unzip it.
2. Drag **Cellar** into **Applications** and open it.
3. The first time, macOS says it can't check the app, because Cellar isn't notarized by Apple. Click **Done**, go to **System Settings → Privacy & Security**, scroll down, click **Open Anyway** next to Cellar, and confirm. You only do this once.

## 3. Get a runtime

1. Click the **Runtimes** button in the dock at the bottom-left of the sidebar.
2. Click **Download** on the runtime you need. You can have both.
3. Wait for the download, then **Unpacking…**, then **✓ Installed**. On a fast connection that's under a minute.

| | **Wine Staging** (184 MB) | **Game Porting Toolkit** (228 MB) |
|---|---|---|
| **Steam** | ✅ Use this one | ❌ The current Steam client crashes on it |
| DirectX 11 games | ✅ through DXVK | ✅ through D3DMetal, faster |
| DirectX 12 games | ❌ No good path yet | ✅ through D3DMetal |
| DirectX 9 and older games, regular apps | ✅ | ✅ |
| Macs | Apple silicon and Intel | Apple silicon only |
| Best for | **Steam** and its games | Games from installers (GOG, standalone) |

## 4. Create a bottle

1. Press **⌘N**, or click **+** in the dock (⌘K) and pick **New Bottle**.
2. Name it (for example "Steam"), choose **Wine Staging** for Steam, keep **Windows 10**, then click **Create**.
3. Wait until **Setting up Windows…** goes away, about 25 seconds.

**What's a bottle?** A separate Windows install with its own C: drive and settings. One bottle can hold Steam and all its games. Give launchers (Epic, EA, Battle.net) and any game that needs special settings a bottle of their own. Bottles are listed in the sidebar.

## 5. Install your games

### From Steam (in a Wine Staging bottle)
1. Click **Install Steam** on the bottle's page, or **+** in the dock → **Install Steam**. Cellar then:
   - installs Steam
   - lets it update itself (about 330 MB, a few minutes, shown as **Updating Steam…**)
   - puts in the fix that lets Steam's windows draw
   - pins Steam to the bottle
2. Open **Steam**, sign in (the QR code with the Steam mobile app works, and Steam Guard may ask you to confirm a new device), then install games as you would on Windows.
3. Play from Steam. Multiplayer and lobbies work.

> **Always open Steam from Cellar.** Steam's updates undo the fix that lets its windows draw. Cellar puts it back every time it opens Steam, so open Steam from Cellar, not from anywhere else.

### From an installer (GOG, standalone games)
1. Click **Run Program…** (⌘O), or **+** in the dock → **Run Program**, and pick the game's `setup.exe` or `.msi`.
2. Go through the installer. When it closes, the game appears in the bottle.

## 6. Play

A bottle's programs are a wheel of covers: Steam games show their box art, everything else a cover made from its icon.
- **Pick a game:** click a cover, use the **‹ ›** buttons, or press **← →**.
- **Start it:** **Play**, click the centred cover again, or press **Return**.
- **More:** the **⋯ Options** button, or right-click a cover:
  - **Launch Options…**, for example `-dx11` or `-windowed`
  - **Pin to Top / Unpin**
  - **Show in Finder**
- **Search:** the search button in the dock (⌘F) filters the bottle's programs by name.

While something runs, it's listed under **Running** with **Log** and **Quit**. **Stop All** closes everything in the bottle.

**Microphone:** the first time a game or Steam uses it, macOS asks whether Cellar can use the microphone. Click **Allow**. Test it in **Steam → Settings → Voice → Test Microphone**.

**Headphones:** Windows programs keep the sound output they started with. Connect headphones **before** opening Steam or a game. If you switch while playing, Cellar shows a reminder: quit the game and open it again.

### The dock

| Button | Shortcut | Does |
|---|---|---|
| Search | ⌘F | Filters the bottle's programs |
| **+** | ⌘K | Frosts the window and shows action tiles: Run Program, New Bottle, Install Steam (until Steam is installed), C: Drive, Wine Settings. With no bottle open: New Bottle and Runtimes. Press a tile's number to pick it, **Esc** to close |
| Runtimes | | Download or remove runtimes |

---

## Bottle settings

On each bottle's page, under **Settings**. They apply the next time a program starts.

| Setting | What it does | Default |
|---|---|---|
| Windows version | The version programs see (10, 8.1, 7, XP) | Windows 10 |
| Synchronization | MSync, ESync or Off. MSync is fastest on macOS | MSync |
| Retina mode | Full display resolution: sharper, harder on the GPU | Off |
| Metal performance HUD | Frame rate and GPU time over games | Off |
| Advertise AVX | For newer games that won't start without AVX | Off |
| **DXVK** (Wine Staging) | DirectX 10 and 11 through DXVK. Needed for DirectX 11 games | **On** |
| Ray tracing (Game Porting Toolkit) | DirectX 12 ray tracing through D3DMetal, M3 or later | Off |

## Updating Cellar

- **1.2.5 and later** update themselves. When there's a new version, a card offers **Update and Restart**. Cellar also checks once a day when it opens, and on **Cellar → Check for Updates…**.
- Updates are signed, and Cellar checks the signature before installing anything. Open games keep running while Cellar restarts.
- **1.2.4 and older:** download the [latest release](https://github.com/alimicious/cellar-releases/releases/latest), then drag the new **Cellar** into **Applications**, choosing **Replace**, and click **Open Anyway** once more.
- Your bottles, runtimes, Steam and games stay where they are.

---

## If a game won't start

Try these in order.

| Symptom | Try |
|---|---|
| Steam's window is black | **Wine Tools → Stop All Windows Programs**, then open Steam from Cellar again |
| Steam opens for a few seconds, then closes | The bottle uses the Game Porting Toolkit. Make a **Wine Staging** bottle for Steam |
| "Failed to load steamui.dll" | Steam's first update never ran. Click OK, **Wine Tools → Stop All Windows Programs**, then open Steam from Cellar: it finishes the update before Steam opens (1.2.1 and later) |
| "Failed to initialize graphics" or a DirectX 11 error (Wine Staging) | Check **DXVK** is on in the bottle's settings |
| DirectX 12 game won't start (Wine Staging) | Launch Options `-dx11` if the game has it. Otherwise it needs a Game Porting Toolkit bottle, without Steam |
| Microphone doesn't work | Allow it when macOS asks. If you clicked Don't Allow: **System Settings → Privacy & Security → Microphone → Cellar** on, then restart the game |
| Sound comes out of the speakers with headphones on | Connect headphones before opening Steam or the game, or quit and reopen it after switching |
| Closes right away | Turn on **Advertise AVX** |
| Hangs while starting | Set **Synchronization** to **Off** |
| Old game complains about Windows | Set **Windows version** to **Windows 7** |
| Blurry on a Retina display | Turn on **Retina mode** |
| Something's stuck | **Stop All** |

**Still stuck?** **Wine Tools → Show Logs in Finder**. Each run has a log, and the end of it usually says why it failed. Unity games also keep their own log in the bottle at `drive_c/users/<you>/AppData/LocalLow/<studio>/<game>/Player.log`.

Reporting it? Open an [issue](https://github.com/alimicious/cellar-releases/issues) with the game, what happened, and the end of the log. Logs contain file paths with your Mac's username, so check before you attach one.

---

## Where things are

| What | Where |
|---|---|
| A bottle's C: drive | Bottle page → **C: Drive**, or `~/Library/Application Support/Cellar/Bottles/<id>/drive_c` |
| Steam games | `drive_c/Program Files (x86)/Steam/steamapps/common/` in the bottle |
| Logs | `~/Library/Logs/Cellar/`, one folder per bottle. Cellar keeps each bottle's newest 30, and cuts any log over 16 MB down to its first and last 2 MB |
| Runtimes and DXVK | `~/Library/Application Support/Cellar/Runtimes/` |
| Steam box art cache | `~/Library/Caches/Cellar/Covers/` |

## Removing things

- **A Steam game:** uninstall it in Steam (right-click it → **Manage → Uninstall**), so Steam's library stays in sync.
- **A bottle:** Settings → **Move Bottle to Trash…**. Everything in it goes, including games and any saves stored there. You can put it back from the Trash.
- **A runtime:** Runtimes → **Remove**. Delete the bottles that use it first.
- **Cellar:** quit it, delete Cellar from **Applications**, then delete `~/Library/Application Support/Cellar`, `~/Library/Logs/Cellar` and `~/Library/Caches/Cellar`.
